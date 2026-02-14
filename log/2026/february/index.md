---
layout: default
title: February 2026
permalink: /log/2026/february/
---

<h1>February 2026</h1>

<ul class="log-list">
  {% for post in site.posts %}
    {% assign ym = post.date | date: "%Y-%m" %}
    {% if ym == "2026-02" and post.categories contains "personal-blog" %}
      <li>
        <a href="{{ "/log/2026/february/" | relative_url }}">
        {{ post.date | date: "%b %-d" }} - {{ post.title }}
        </a>
      </li>
    {% endif %}
  {% endfor %}
</ul>
