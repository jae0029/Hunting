---
layout: default
title: Fishing Trips
category: fishing
permalink: /categories/fishing/
---

# Fishing Trips

<ul>
  {% for post in site.categories['fishing'] %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <span>{{ post.date | date: "%B %d, %Y" }}</span>
    </li>
  {% endfor %}
</ul>
