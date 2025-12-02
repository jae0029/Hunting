---
layout: default
title: Turkey Hunts
category: turkey-hunts
---

<h1>Turkey Hunts</h1>

<ul>
  {% for post in site.categories['turkey-hunts'] %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <span>{{ post.date | date: "%B %d, %Y" }}</span>
    </li>
  {% endfor %}
</ul>
