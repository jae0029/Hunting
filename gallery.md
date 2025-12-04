---
layout: default
title: Gallery
permalink: /gallery/
---

<h2>Photo Gallery</h2>
<p>Highlights from hunts and outdoor time with the family.</p>

{% comment %}
  1. Get gallery items from _gallery (with metadata)
  2. Get static images from /assets/images/gallery/
  3. Exclude static images that are already in _gallery
{% endcomment %}

{% assign gallery_items_md = site.gallery | sort: "date" | reverse %}

{% assign gallery_items_static = site.static_files | where_exp: "f", "f.path contains '/assets/images/gallery/'" %}
{% for item in gallery_items_md %}
  {% assign gallery_items_static = gallery_items_static | reject: "path", item.image %}
{% endfor %}

{% assign gallery_items = gallery_items_md | concat: gallery_items_static %}

<!-- Full-width gallery container -->
<div class="gallery-page">
  <div class="gallery">
    {% for item in gallery_items %}
      <figure class="gallery-item">
        {% if item.image %}
          <!-- From MD file -->
          <a href="{{ item.image | relative_url }}" class="lightbox-link" data-index="{{ forloop.index0 }}">
            <img src="{{ item.image | relative_url }}" alt="{{ item.title | default: item.name }}">
          </a>
          <figcaption>
            {% if item.title %}<strong>{{ item.title }}</strong>{% endif %}
            {% if item.caption %}<br>{{ item.caption }}{% endif %}
            {% if item.date %}<br><small>{{ item.date | date: "%B %d, %Y" }}</small>{% endif %}
            {% if item.tags %}<br><small>Tags: {{ item.tags | join: ", " }}</small>{% endif %}
          </figcaption>
        {% else %}
          <!-- From static image -->
          <a href="{{ item.path | relative_url }}" class="lightbox-link" data-index="{{ forloop.index0 }}">
            <img src="{{ item.path | relative_url }}" alt="{{ item.name | split: '.' | first }}">
          </a>
          <figcaption>{{ item.name | split: '.' | first }}</figcaption>
        {% endif %}
      </figure>
    {% endfor %}
  </div>
</div>

<!-- Lightbox and navigation code remains exactly the same as before -->
<!-- ... insert your lightbox HTML, CSS, and JS here ... -->


<!-- Lightbox container -->
<div id="lightbox" class="lightbox">
  <span class="close">&times;</span>
  <img class="lightbox-content" id="lightbox-img">
  <div id="lightbox-caption"></div>
  <a class="prev">&#10094;</a>
  <a class="next">&#10095;</a>
</div>

<style>
/* Lightbox overlay */
.lightbox {
  display: none; 
  position: fixed; 
  z-index: 999; 
  padding-top: 60px; 
  left: 0;
  top: 0;
  width: 100%; 
  height: 100%; 
  overflow: auto; 
  background-color: rgba(0,0,0,0.9); 
}

.lightbox-content {
  margin: auto;
  display: block;
  max-width: 90%;
  max-height: 80%;
}

#lightbox-caption {
  margin: auto;
  display: block;
  width: 80%;
  max-width: 700px;
  text-align: center;
  color: #ccc;
  padding: 10px 0;
}

.close {
  position: absolute;
  top: 20px;
  right: 35px;
  color: #fff;
  font-size: 40px;
  font-weight: bold;
  cursor: pointer;
}

.close:hover { color: #bbb; }

/* Navigation arrows */
.prev, .next {
  cursor: pointer;
  position: absolute;
  top: 50%;
  width: auto;
  margin-top: -30px;
  padding: 16px;
  color: white;
  font-weight: bold;
  font-size: 40px;
  transition: 0.3s;
  user-select: none;
}

.prev { left: 20px; }
.next { right: 20px; }

.prev:hover, .next:hover { color: #bbb; }
</style>

<script>
const lightbox = document.getElementById('lightbox');
const lightboxImg = document.getElementById('lightbox-img');
const lightboxCaption = document.getElementById('lightbox-caption');
const closeBtn = document.getElementsByClassName('close')[0];
const prevBtn = document.getElementsByClassName('prev')[0];
const nextBtn = document.getElementsByClassName('next')[0];

const links = Array.from(document.querySelectorAll('.lightbox-link'));
let currentIndex = 0;

function openLightbox(index) {
  const link = links[index];
  lightbox.style.display = 'block';
  lightboxImg.src = link.href;
  lightboxCaption.textContent = link.querySelector('img').alt || '';
  currentIndex = index;
}

links.forEach((link, i) => {
  link.addEventListener('click', function(e) {
    e.preventDefault();
    openLightbox(i);
  });
});

function showNext() {
  currentIndex = (currentIndex + 1) % links.length;
  openLightbox(currentIndex);
}

function showPrev() {
  currentIndex = (currentIndex - 1 + links.length) % links.length;
  openLightbox(currentIndex);
}

nextBtn.onclick = showNext;
prevBtn.onclick = showPrev;
closeBtn.onclick = () => lightbox.style.display = 'none';
lightbox.onclick = (e) => { if (e.target == lightbox) lightbox.style.display = 'none'; };

// Optional: use keyboard arrows
document.addEventListener('keydown', function(e) {
  if (lightbox.style.display === 'block') {
    if (e.key === 'ArrowRight') showNext();
    if (e.key === 'ArrowLeft') showPrev();
    if (e.key === 'Escape') lightbox.style.display = 'none';
  }
});
</script>
