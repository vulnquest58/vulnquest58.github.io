---
layout: default
title: Home
description: "VulnQuest - Offensive Security Portfolio specializing in Bug Bounty, Red Teaming, Tools Development, and CTF Challenges"
---

<section class="hero">
  <div class="container">
    <h1 class="hero-title">🛡️ VulnQuest</h1>
    <p class="hero-subtitle">Offensive Security Portfolio</p>
    <p class="hero-description">
      Exploring the depths of cybersecurity through Bug Bounty hunting, Red Team operations, 
      custom tool development, and CTF challenges. Documenting the journey of finding vulnerabilities 
      and building offensive security solutions.
    </p>
    <div class="hero-buttons">
      <a href="{{ '/bugbounty/' | relative_url }}" class="btn btn-primary">
        <i class="fas fa-bug"></i> Explore Bug Bounty
      </a>
      <a href="{{ '/tools/' | relative_url }}" class="btn btn-secondary">
        <i class="fas fa-tools"></i> View Tools
      </a>
    </div>
  </div>
</section>

<section class="section">
  <div class="container">
    <h2 class="section-title">What I Do</h2>
    <div class="cards-grid">
      
      <div class="card">
        <div class="card-icon"><i class="fas fa-bug"></i></div>
        <h3 class="card-title">Bug Bounty</h3>
        <p class="card-description">
          Professional bug bounty hunting with detailed writeups, methodologies, 
          and proven track record across multiple platforms.
        </p>
        <a href="{{ '/bugbounty/' | relative_url }}" class="card-link">
          Learn More <i class="fas fa-arrow-right"></i>
        </a>
      </div>
      
      <div class="card">
        <div class="card-icon"><i class="fas fa-user-ninja"></i></div>
        <h3 class="card-title">Red Teaming</h3>
        <p class="card-description">
          Advanced red team operations including C2 frameworks, evasion techniques, 
          and full-scope adversary simulations.
        </p>
        <a href="{{ '/redteam/' | relative_url }}" class="card-link">
          Learn More <i class="fas fa-arrow-right"></i>
        </a>
      </div>
      
      <div class="card">
        <div class="card-icon"><i class="fas fa-tools"></i></div>
        <h3 class="card-title">Tools Development</h3>
        <p class="card-description">
          Custom security tools including VULNTRACE, Kali Master Framework, 
          Lab Manager, and various automation scripts.
        </p>
        <a href="{{ '/tools/' | relative_url }}" class="card-link">
          Learn More <i class="fas fa-arrow-right"></i>
        </a>
      </div>
      
      <div class="card">
        <div class="card-icon"><i class="fas fa-flag"></i></div>
        <h3 class="card-title">CTF Challenges</h3>
        <p class="card-description">
          Solutions and writeups for challenges from HackTheBox, TryHackMe, 
          PortSwigger, and other CTF platforms.
        </p>
        <a href="{{ '/ctf/' | relative_url }}" class="card-link">
          Learn More <i class="fas fa-arrow-right"></i>
        </a>
      </div>
      
      <div class="card">
        <div class="card-icon"><i class="fas fa-flask"></i></div>
        <h3 class="card-title">Security Labs</h3>
        <p class="card-description">
          30+ custom security labs covering web applications, Active Directory, 
          mobile security, and cloud environments.
        </p>
        <a href="{{ '/labs/' | relative_url }}" class="card-link">
          Learn More <i class="fas fa-arrow-right"></i>
        </a>
      </div>
      
      <div class="card">
        <div class="card-icon"><i class="fas fa-blog"></i></div>
        <h3 class="card-title">Blog & Research</h3>
        <p class="card-description">
          Technical articles, research findings, tutorials, and insights 
          from the offensive security field.
        </p>
        <a href="{{ '/blog/' | relative_url }}" class="card-link">
          Learn More <i class="fas fa-arrow-right"></i>
        </a>
      </div>
      
    </div>
  </div>
</section>

<section class="section">
  <div class="container">
    <h2 class="section-title">Latest Updates</h2>
    <div class="cards-grid">
      {% for post in site.posts limit:3 %}
        <div class="card">
          <div class="card-icon"><i class="fas fa-newspaper"></i></div>
          <h3 class="card-title">{{ post.title }}</h3>
          <p class="card-description">{{ post.excerpt | strip_html | truncate: 150 }}</p>
          <a href="{{ post.url | relative_url }}" class="card-link">
            Read More <i class="fas fa-arrow-right"></i>
          </a>
        </div>
      {% endfor %}
    </div>
  </div>
</section>
