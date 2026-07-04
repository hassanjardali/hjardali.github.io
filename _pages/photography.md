---
layout: single
title: "Photography"
permalink: /photography/
author_profile: false
---

{% include base_path %}

A few frames from where I've been. Click any photo to view it larger.

<nav class="photo-nav">
  {% for region in site.data.photography.regions %}
    <a href="#{{ region.id }}">{{ region.name }}</a>
  {% endfor %}
</nav>

{% for region in site.data.photography.regions %}
  <section class="region" id="{{ region.id }}">
    <h2 class="region__title">{{ region.name }}</h2>
    <div class="masonry masonry--photos">
      {% for photo in region.photos %}
        {% assign src = photo.file | prepend: '/images/photography/' | prepend: base_path %}
        <figure class="photo-card">
          <img src="{{ src }}" alt="{{ photo.caption | escape }}" loading="lazy"
               {% if photo.width and photo.height %}width="{{ photo.width }}" height="{{ photo.height }}"{% endif %}
               data-zoom data-full="{{ src }}" data-caption="{{ photo.caption | escape }}">
          {% if photo.caption and photo.caption != "" %}
            <figcaption>{{ photo.caption }}</figcaption>
          {% endif %}
        </figure>
      {% endfor %}
    </div>
  </section>
{% endfor %}

{% include lightbox.html %}
