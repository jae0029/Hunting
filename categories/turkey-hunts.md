---
layout: default
title: Turkey Hunts
permalink: /categories/turkey-hunts/
---

# Turkey Hunts


<ul>
  {% for post in site.categories['turkey-hunts'] %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <span>{{ post.date | date: "%B %d, %Y" }}</span>
    </li>
  {% endfor %}
</ul>
