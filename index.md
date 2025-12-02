---
layout: home
title: "Home"
---

<h1>Hunting Stories</h1>
<ul>
{% for post in site.posts %}
  <li>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    <span> - {{ post.date | date: "%m-%d-%Y" }}</span>
    {% if post.excerpt %}
      <p>{{ post.excerpt }}</p>
    {% endif %}
  </li>
{% endfor %}
</ul>
