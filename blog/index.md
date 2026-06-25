---
layout: page
title: Security Blog & Research
subtitle: Technical articles, walkthroughs, and research findings
description: "Security articles, analysis, and research findings in offensive security."
---

## Technical Articles

Welcome to my blog! Here I publish deep dives, research papers, and technical articles on various offensive security topics.

<div class="posts-list">
  {% for post in site.posts %}
    <div class="card" style="margin-bottom: var(--spacing-md);">
      <div class="post-meta" style="margin-bottom: var(--spacing-sm);">
        <span><i class="far fa-calendar"></i> {{ post.date | date: "%B %d, %Y" }}</span>
        {% if post.category %}
          <span class="tag">{{ post.category }}</span>
        {% endif %}
      </div>
      <h3 class="card-title"><a href="{{ post.url | relative_url }}" style="color: var(--accent-primary); text-decoration: none;">{{ post.title }}</a></h3>
      <p class="card-description">{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
      <a href="{{ post.url | relative_url }}" class="card-link">Read Full Post <i class="fas fa-arrow-right"></i></a>
    </div>
  {% else %}
    <p>No posts published yet. Stay tuned!</p>
  {% endfor %}
</div>
