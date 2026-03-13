---
layout: default
title: March 2026
permalink: /log/2026/march/
---

<h1>March 2026</h1>

<ul class="log-list">
  {% for post in site.posts %}
    {% assign ym = post.date | date: "%Y-%m" %}
    {% if ym == "2026-03" and post.categories contains "personal-blog" %}
      <li>
        <a href="{{ post.url | relative_url }}">
        {{ post.date | date: "%b %-d" }} - {{ post.title }}
        </a>
      </li>
    {% endif %}
  {% endfor %}
</ul>
