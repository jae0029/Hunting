---
layout: default
title: Other Stories
category: other-stories
permalink: /categories/other-stories/
---

# Other Stories

<ul>
  {% for post in site.categories['other-stories'] %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <span>{{ post.date | date: "%B %d, %Y" }}</span>
    </li>
  {% endfor %}
</ul>
