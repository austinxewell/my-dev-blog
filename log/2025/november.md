---
layout: default
title: November 2025
---

<h1>November 2025</h1>

<ul class="log-list">
  {% for post in site.posts %}
    {% assign ym = post.date | date: "%Y-%m" %}
    {% if ym == "2025-11" and post.categories contains "personal-blog" %}
      <li>
        <a href="{{ post.url | relative_url }}">
          {{ post.date | date: "%b %-d" }} – {{ post.title }}
        </a>
      </li>
    {% endif %}
  {% endfor %}
</ul>
