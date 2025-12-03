---
layout: default
title: Gallery
permalink: /gallery/
---

<h2>Photo Gallery</h2>
<p>Highlights from hunts and outdoor time with the family.</p>

<!-- Optional filter controls (by year or tag) -->
{% assign tag = page.tag | default: '' %}
{% assign year = page.year | default: '' %}

{% comment %}
  Build a filtered list:
  - Filter by tag if provided: /gallery/?tag=doe
  - Filter by year if provided: /gallery/?year=2025
{% endcomment %}
{% assign items = site.gallery %}

{% if tag != '' %}
  {% assign items = items | where_exp: "item", "item.tags and item.tags contains tag" %}
{% endif %}
{% if year != '' %}
  {% assign items = items | where_exp: "item", "item.date and item.date contains year" %}
{% endif %}

<!-- Sort newest first if date is present -->
{% assign items = items | sort: "date" | reverse %}

<!-- Empty state -->
{% if items.size == 0 %}
  <p><em>No images found. Add entries to <code>_gallery/</code> with an <code>image</code> path.</em></p>
{% endif %}

<div class="gallery">
  {% for item in items %}
    <figure class="gallery-item">
      {{ item.image | relative_url }}
      {% if item.title or item.caption %}
        <figcaption>
          {% if item.title %}<strong>{{ item.title }}</strong>{% endif %}
          {% if item.caption %}<br>{{ item.caption }}{% endif %}
          {% if item.date %}<br><small>{{ item.date | date: "%B %d, %Y" }}</small>{% endif %}
          {% if item.tags %}<br><small>Tags: {{ item.tags | join: ", " }}</small>{% endif %}
        </figcaption>
      {% endif %}
    </figure>
  {% endfor %}
</div>
