---
layout: default
title: Personal Log
nav: true
---

<h1>Personal Log</h1>

{% assign posts_by_year = site.posts | group_by_exp:"post","post.date | date: '%Y'" %}

{% for year in posts_by_year %}

  <h2>{{ year.name }}</h2>

{% assign posts_by_month = year.items | group_by_exp:"post","post.date | date: '%m'" %}

  <ul>
    {% for month in posts_by_month %}
      {% assign month_number = month.name %}
      {% assign month_name = month.items[0].date | date: "%B" %}

      <li>
        <a href="/log/{{ year.name }}/{{ month_name | downcase }}/">
          {{ month_name }}
        </a>
      </li>
    {% endfor %}

  </ul>
{% endfor %}
