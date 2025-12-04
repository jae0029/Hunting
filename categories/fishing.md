---
layout: default
title: Fishing
permalink: /categories/fishing/
---

<div class="home-container">
  <h1>{{ page.title }}</h1>

  <ul class="post-list">
    {% assign category_posts = site.categories['fishing'] %}
    {% for post in category_posts %}
      <li class="post-item">
        <article class="post-card">
          <div class="post-content">
            <!-- Post title -->
            <h2 class="post-title">
              <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
            </h2>

            <!-- Post date -->
            <p class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</p>

            <!-- Post excerpt -->
            {% if post.excerpt %}
              <p class="post-excerpt">{{ post.excerpt }}</p>
            {% endif %}

            <!-- Read more link -->
            <a class="read-more" href="{{ post.url | relative_url }}">Read More →</a>
          </div>

          <!-- Featured image -->
          {% if post.featured_image %}
            <div class="post-image">
              <a href="{{ post.url | relative_url }}">
                <img src="{{ post.featured_image | relative_url }}" alt="{{ post.title }}">
              </a>
            </div>
          {% endif %}
        </article>
      </li>
    {% endfor %}
  </ul>
</div>

<style>
/* General list styles */
.post-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.post-item {
  margin-bottom: 0.25rem; /* less vertical space between cards */
}

/* Card styles */
.post-card {
  display: flex;
  flex-direction: row;
  align-items: stretch; /* make content and image same height */
  border: 1px solid #ddd;
  padding: 0.75rem 1rem; /* reduce vertical padding */
  border-radius: 8px;
  background: #fff;
  gap: 1.5rem; /* slightly less gap between image and text */
}

/* Text content */
.post-content {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-between; /* pushes Read More to bottom if content is taller */
}

/* Featured image */
.post-image {
  flex-shrink: 0;
  display: flex;
  align-items: center;
}

.post-image img {
  width: 180px; /* slightly smaller image */
  height: 100%; /* match text height */
  object-fit: cover;
  border-radius: 8px;
}

/* Responsive layout for smaller screens */
@media (max-width: 600px) {
  .post-card {
    flex-direction: column; /* stack image above text */
    align-items: center;
    padding: 0.5rem 0.75rem; /* reduce padding further on small screens */
  }

  .post-image img {
    width: 100%;
    max-width: 250px; /* smaller max-width */
    height: auto;
    object-fit: cover;
  }

  .post-image {
    width: 100%;
    display: flex;
    justify-content: center;
    margin-bottom: 0.5rem; /* add small spacing between image and text */
  }
}
</style>
