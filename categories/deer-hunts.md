---
layout: default
title: Deer Hunts
permalink: /categories/deer-hunts/
---

<div class="home-container">
  <h1>{{ page.title }}</h1>

  <ul class="post-list">
    {% assign category_posts = site.categories['deer-hunts'] %}
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
  margin-bottom: 2rem;
}

/* Card styles */
.post-card {
  display: flex;
  flex-direction: row;
  align-items: stretch; /* make content and image same height */
  border: 1px solid #ddd;
  padding: 1rem;
  border-radius: 8px;
  background: #fff;
  gap: 1rem;
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
  width: 200px; /* smaller size */
  height: 100%; /* match text height */
  object-fit: cover;
  border-radius: 8px;
}

/* Responsive layout for smaller screens */
@media (max-width: 768px) {
  .post-card {
    flex-direction: column;
  }
  .post-image img {
    width: 100%;
    height: auto;
  }
}
</style>
