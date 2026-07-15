---
permalink: /gallery/
title: "Gallery"
author_profile: true
---

Welcome to our team gallery, where we share moments from team gatherings, academic activities, and our journey together.

{% assign team_photo_count = 0 %}
{% for photo in site.static_files %}
  {% if photo.path contains '/images/team/' %}
    {% assign extension = photo.extname | downcase %}
    {% if extension == '.jpg' or extension == '.jpeg' or extension == '.png' or extension == '.webp' %}
      {% assign team_photo_count = team_photo_count | plus: 1 %}
    {% endif %}
  {% endif %}
{% endfor %}

{% if team_photo_count > 0 %}
<div class="team-gallery">
  {% for photo in site.static_files %}
    {% if photo.path contains '/images/team/' %}
      {% assign extension = photo.extname | downcase %}
      {% if extension == '.jpg' or extension == '.jpeg' or extension == '.png' or extension == '.webp' %}
        <figure class="team-gallery__item">
          <img src="{{ photo.path | relative_url }}" alt="Team gathering" loading="lazy">
        </figure>
      {% endif %}
    {% endif %}
  {% endfor %}
</div>
{% else %}
<p class="notice--info">Team photos will be added soon.</p>
{% endif %}

<style>
.team-gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: 1.25rem;
  margin-top: 1.5rem;
}

.team-gallery__item {
  margin: 0;
  overflow: hidden;
  border-radius: 0.5rem;
  background: #f3f3f3;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.team-gallery__item img {
  display: block;
  width: 100%;
  height: auto;
  transition: transform 0.25s ease;
}

.team-gallery__item:hover img {
  transform: scale(1.03);
}
</style>
