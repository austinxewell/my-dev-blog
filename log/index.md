---
layout: default
title: Personal Log
nav: true
---

<h1>Personal Log</h1>

{% assign current_year = site.time | date: "%Y" %}
{% assign current_month = site.time | date: "%m" %}
{% assign current_month_name = site.time | date: "%B" %}

<h2>{{ current_month_name }} {{ current_year }}</h2>

<ul class="log-list">
  {% for post in site.posts %}
    {% assign post_year = post.date | date: "%Y" %}
    {% assign post_month = post.date | date: "%m" %}

    {% if post_year == current_year and post_month == current_month and post.categories contains "personal-blog" %}
      <li>
        <a href="{{ post.url | relative_url }}">
          {{ post.date | date: "%b %-d" }} - {{ post.title }}
        </a>
      </li>
    {% endif %}

{% endfor %}

</ul>

<hr />

{% assign posts_by_year = site.posts | group_by_exp: "post", "post.date | date: '%Y'" %}

{% for year in posts_by_year %}

  <h2>{{ year.name }}</h2>

{% assign posts_by_month = year.items | group_by_exp: "post", "post.date | date: '%m'" %}

  <ul>
    {% for month in posts_by_month %}
      {% assign month_number = month.name %}
      {% assign month_name = '2020-' | append: month_number | append: '-01' | date: "%B" %}

      {% if year.name != current_year or month_number != current_month %}
        {% assign month_url = site.baseurl | append: '/log/' | append: year.name | append: '/' | append: month_name | downcase | append: '/' %}
        <li>
          <a href="{{ month_url }}">
            {{ month_name }}
          </a>
        </li>
      {% endif %}
    {% endfor %}

  </ul>
{% endfor %}
