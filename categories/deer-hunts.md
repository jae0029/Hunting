---
layout: default
title: Deer Hunts
category: deer-hunts
permalink: /categories/deer-hunts/
---

# Deer Hunts

<ul>
  {% for post in site.categories['deer-hunts'] %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <span>{{ post.date | date: "%B %d, %Y" }}</span>
    </li>
  {% endfor %}
</ul>
