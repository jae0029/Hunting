---
layout: default
title: Other Stories
category: other-stories
---

<h1>Other Stories</h1>

<ul>
  {% for post in site.categories['other-stories'] %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <span>{{ post.date | date: "%B %d, %Y" }}</span>
    </li>
  {% endfor %}
</ul>
