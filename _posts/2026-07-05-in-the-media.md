---
title: "In the Media"
date: 2026-07-05
permalink: /posts/2026/07/in-the-media/
excerpt: "Press and media coverage — from autonomous racing to earlier photography, Model UN, and competitions."
tags:
  - media
  - press
---

Coverage of my work — from autonomous racing today, back to photography, Model UN, and competitions in my high-school years.

{% for cat in site.data.media.categories %}
  <section class="media-cat" id="{{ cat.id }}">
    <h2 class="section-title">{{ cat.name }}</h2>
    <ul class="media-list">
      {% assign items = cat.items | sort: 'date' | reverse %}
      {% for m in items %}
        <li class="media-item">
          <span class="media-date">{{ m.label }}</span>
          <span class="media-body">
            <a class="media-title" href="{{ m.url }}" target="_blank" rel="noopener">{{ m.title }}<span class="pub-arrow">↗</span></a>
            <span class="media-outlet">{{ m.outlet }}</span>
          </span>
        </li>
      {% endfor %}
    </ul>
  </section>
{% endfor %}
