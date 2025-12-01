
---
layout: default
title: "Home"
---

# Welcome to My Hunting Blog

Here you'll find stories from my hunting adventures. Check out the latest posts below:

<ul>
  {% assign posts_sorted = site.posts | sort: "date" | reverse %}
  {% for post in posts_sorted %}
    <li>
      {{ post.url | relative_url }}{{ post.title }}</a>
      — <span>{{ post.date | date: "%m-%d-%Y" }}</span>
      {% if post.excerpt %}
        <br><small>{{ post.excerpt | strip_html | truncate: 160 }}</small>
      {% endif %}
    </li>
  {% endfor %}
</ul>
