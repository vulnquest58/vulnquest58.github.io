---
layout: page
title: Mobile Security Lab
subtitle: Environment for Android & iOS security testing
---

## Lab Setup & Equipment

The Mobile Security Lab is configured to perform deep analysis of Android and iOS applications (APKs and IPAs), covering static code analysis, dynamic analysis, SSL pinning bypasses, and local storage auditing.

### Tools & Instrumentation

*   **Android Testing**:
    *   **Emulator**: Genymotion / Android Studio AVD running rooted Android images.
    *   **Physical Device**: Rooted Pixel 4a running custom LineageOS.
    *   **Software**: Frida-server installed on the device for runtime hooking.
*   **iOS Testing**:
    *   **Physical Device**: Jailbroken iPhone 8 running iOS 14.8 with unc0ver / checkra1n.
    *   **Instrumentation**: Cydia Substrate, Frida-server, and OpenSSH for shell access.
*   **Analysis Workstation Tools**:
    *   **Static Analysis**: Jadx-gui, MobSF (Mobile Security Framework), Hopper Disassembler, IDA Pro.
    *   **Dynamic Instrumentation**: Frida-tools, Objection, Burp Suite (configured with device proxy and system CA certificate).

---

## Testing Methodologies

### 1. SSL Pinning Bypass
Many modern mobile apps refuse to connect if a custom CA certificate (like Burp's) is in the trust store.
*   **Methodology**:
    1.  Inspect the app using `jadx-gui` to find pinning code (e.g., TrustManager, OkHttpClient).
    2.  Inject a custom Frida script via Objection to hook the network library:
        ```bash
        objection --gadget "com.target.app" explore
        android sslpinning disable
        ```
    3.  Route traffic through Burp Suite to intercept API requests.

### 2. Local Storage Auditing
Auditing what sensitive data is written locally on the device flash.
*   **Methodology**:
    1.  Access the application data directory on the device:
        *   **Android**: `/data/data/com.target.app/`
        *   **iOS**: `/var/mobile/Containers/Data/Application/[UUID]/`
    2.  Analyze files for cleartext credentials, session keys, or PII:
        *   **SQLite databases**: View files using `sqlite3`.
        *   **Shared Preferences / Plists**: View XML/Binary plist configuration files.
        *   **Local Caches**: Audit temp files and cache storage.
