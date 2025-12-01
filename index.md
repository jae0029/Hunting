
---
layout: default
title: "Home"
---

# Welcome to My Hunting Blog

Here you'll find stories from my hunting adventures. Check out the latest posts below:

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a> - {{ post.date | date: "%B %d, %Y" }}
 {% endfor %}
</ul>
