# 🛡️ VulnQuest — Offensive Security Portfolio

[![Jekyll](https://img.shields.io/badge/Jekyll-4.x-red?logo=jekyll)](https://jekyllrb.com/)
[![GitHub Pages](https://img.shields.io/badge/GitHub_Pages-Active-success?logo=github)](https://pages.github.com/)
[![License](https://img.shields.io/badge/License-MIT-blue)](LICENSE)

> A professional offensive security portfolio documenting Bug Bounty, Red Team Operations, Custom Tool Development, CTF Challenges, and Security Labs.

🌐 **Live Site**: [vulnquest58.github.io](https://vulnquest58.github.io)

---

## 📁 Project Structure

```
vulnquest/
├── _config.yml                 # Jekyll site configuration
├── _layouts/
│   ├── default.html            # Main layout with header/footer
│   ├── page.html               # Standard page layout
│   └── post.html               # Blog post layout
├── _includes/
│   ├── header.html             # Site navigation header
│   ├── footer.html             # Site footer with social links
│   └── navigation.html         # Breadcrumb navigation component
├── _posts/                     # Blog posts (YYYY-MM-DD-title.md)
├── assets/
│   ├── css/style.css           # Main stylesheet (dark theme)
│   └── js/main.js              # Main JavaScript (mobile nav, etc.)
├── about/                      # About section pages
│   ├── index.md                # Main about page
│   ├── skills.md               # Technical skills breakdown
│   ├── certifications.md       # Security certifications
│   └── contact.md              # Contact & PGP info
├── bugbounty/                  # Bug Bounty section
│   ├── index.md                # Bug bounty overview
│   ├── methodology.md          # Hunting methodology guide
│   ├── writeups/               # Vulnerability writeups
│   └── tools/                  # Tools used for bug hunting
├── redteam/                    # Red Team section
│   ├── index.md                # Red team overview
│   ├── c2-frameworks/          # C2 framework guides (Sliver, Havoc, etc.)
│   ├── tradecraft/             # Evasion & tradecraft techniques
│   └── operations/             # Anonymized operation journals
├── ctf/                        # CTF Challenges section
│   ├── index.md                # CTF overview
│   ├── platforms/              # Platform-specific writeups (HTB, THM, PS)
│   ├── challenges/             # Challenge directory by category
│   └── writeups/               # Chronological writeups index
├── tools/                      # Custom Tools section
│   ├── index.md                # Tools overview
│   ├── vulntrace/              # VULNTRACE documentation
│   ├── kali-master/            # Kali Master documentation
│   ├── lab-manager/            # Lab Manager documentation
│   └── custom-scripts/         # Custom scripts collection
├── labs/                       # Security Labs section
│   ├── index.md                # Labs overview
│   ├── ad-labs.md              # Active Directory lab details
│   ├── web-labs.md             # Web application lab details
│   ├── cloud-labs.md           # Cloud (AWS/Azure) lab details
│   └── mobile-labs.md          # Mobile security lab details
├── blog/                       # Blog & Research section
│   └── index.md                # Blog listing page
├── 404.html                    # Custom 404 error page
├── index.md                    # Home page
├── Gemfile                     # Ruby gem dependencies
└── .github/
    └── workflows/
        └── jekyll.yml          # GitHub Actions CI/CD deployment
```

---

## 🚀 Quick Start (Local Development)

### Prerequisites

- **Ruby** >= 3.0
- **Bundler** >= 2.0
- **Git**

### Setup

```bash
# 1. Clone the repository
git clone https://github.com/vulnquest58/vulnquest.github.io.git
cd vulnquest.github.io

# 2. Install dependencies
bundle install

# 3. Run the local development server
bundle exec jekyll serve --livereload

# 4. Open in browser
# Navigate to http://localhost:4000
```

### Build for Production

```bash
bundle exec jekyll build
# Output will be in the _site/ directory
```

---

## 🎨 Design System

The site uses a custom dark theme built with vanilla CSS:

| Token | Value | Usage |
|---|---|---|
| `--color-bg` | `#0a0e27` | Page background |
| `--color-surface` | `#0f1535` | Card/panel backgrounds |
| `--color-primary` | `#00ff88` | Primary actions, accent |
| `--color-secondary` | `#4ecdc4` | Secondary elements |
| `--color-text` | `#c8d6f0` | Body text |
| `--font-sans` | Inter | UI text |
| `--font-mono` | JetBrains Mono | Code blocks |
| `--font-ar` | Cairo | Arabic text (RTL support) |

---

## 🔄 Deployment

The site is automatically deployed to GitHub Pages via **GitHub Actions** on every push to the `main` branch.

The workflow file at [`.github/workflows/jekyll.yml`](.github/workflows/jekyll.yml) handles:
1. Checkout and Ruby setup
2. Bundle install
3. Jekyll build
4. Deployment to `gh-pages` branch

---

## 📝 Adding Content

### New Blog Post

```bash
# Create a new post file
touch _posts/YYYY-MM-DD-post-title.md
```

```yaml
---
layout: post
title: "Your Post Title"
date: YYYY-MM-DD
categories: [bugbounty, redteam, ctf]
tags: [xss, ssrf, active-directory]
---

Your post content here...
```

### New Bug Bounty Writeup

Copy the template and fill in the details:

```bash
cp bugbounty/writeups/_template.md bugbounty/writeups/your-writeup.md
```

### New Tool Page

```bash
cp tools/_template.md tools/your-tool/index.md
```

---

## 🤝 Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for contribution guidelines and code of conduct.

---

## ⚖️ License

This project is licensed under the MIT License — see [LICENSE](LICENSE) for details.

All security research and writeups are published after responsible disclosure. Techniques documented here are for **authorized testing and educational purposes only**.

---

<p align="center">Built with ❤️ and ⚔️ by <a href="https://github.com/vulnquest58">VulnQuest58</a></p>
