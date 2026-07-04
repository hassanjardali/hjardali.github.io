---
permalink: /
title: false
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

{% include base_path %}

<div class="home-intro" markdown="1">
I'm a **robotics PhD student at Indiana University** in Bloomington, in the
[Vehicle Autonomy & Intelligence Lab](https://vail-robotics.net), advised by
**Professor Lantao Liu**. My focus is **planning and control** for autonomous
systems.

My research began in **field robotics** — terrain traversability analysis and
autonomous navigation over uneven, unstructured terrain. It now centers on
**planning and control for autonomous racing**, pushing full-scale race cars to
the limits of speed and control. I'm the **current lead of the IU-Luddy
Autonomous Racing team**, which competes in the Indy Autonomous Challenge.

Reach me at [hjardali@iu.edu](mailto:hjardali@iu.edu), or find me on
[Google Scholar](https://scholar.google.com/citations?user=SPkVT4IAAAAJ&hl=en),
[LinkedIn](https://www.linkedin.com/in/hassan-jardali/), and
[GitHub](https://github.com/hassanjardali).
</div>

<section id="timeline" class="home-section">
  <h2 class="section-title">Timeline</h2>
  <ol class="timeline">
    {% assign events = site.data.news | sort: 'date' | reverse %}
    {% for item in events %}
      <li class="timeline__item timeline__item--{{ item.type | default: 'milestone' }}">
        <span class="timeline__date">{{ item.label }}</span>
        <span class="timeline__text">{{ item.text | markdownify | remove: '<p>' | remove: '</p>' }}</span>
      </li>
    {% endfor %}
  </ol>
</section>

<section id="publications" class="home-section">
  <h2 class="section-title">Publications</h2>
  <p class="section-note">Click a title to open the paper. All work is also on my
    <a href="https://scholar.google.com/citations?user=SPkVT4IAAAAJ&hl=en">Google Scholar profile</a>.</p>
  <ol class="pub-list">
    {% assign pubs = site.publications | sort: 'date' | reverse %}
    {% for pub in pubs %}
      {% assign media = pub.gif | default: '/images/pubs/placeholder.gif' | prepend: base_path %}
      {% if media contains '.mp4' or media contains '.webm' %}
        {% capture media_tag %}<video src="{{ media }}" autoplay muted loop playsinline preload="metadata"></video>{% endcapture %}
      {% else %}
        {% capture media_tag %}<img src="{{ media }}" alt="" loading="lazy">{% endcapture %}
      {% endif %}
      <li class="pub">
        {% if pub.video %}
          <button class="pub__thumb pub__thumb--video" type="button" data-video="{{ pub.video }}"{% if pub.video_start %} data-start="{{ pub.video_start }}"{% endif %} aria-label="Play video for {{ pub.title | escape }}">
            {{ media_tag }}
            <span class="pub__play" aria-hidden="true"></span>
          </button>
        {% elsif pub.paperurl %}
          <a class="pub__thumb" href="{{ pub.paperurl }}" target="_blank" rel="noopener" tabindex="-1" aria-hidden="true">
            {{ media_tag }}
          </a>
        {% else %}
          <span class="pub__thumb">
            {{ media_tag }}
          </span>
        {% endif %}
        <div class="pub__body">
          {% if pub.paperurl %}
            <a class="pub-title" href="{{ pub.paperurl }}" target="_blank" rel="noopener">{{ pub.title }}<span class="pub-arrow">↗</span></a>
          {% else %}
            <span class="pub-title">{{ pub.title }}</span>
          {% endif %}
          <div class="pub-authors">{{ pub.authors | replace: 'H. Jardali', '<strong>H. Jardali</strong>' }}</div>
          <div class="pub-meta">{{ pub.venue }}{% if pub.date %} · {{ pub.date | date: "%Y" }}{% endif %}{% if pub.status %} · {{ pub.status }}{% endif %}</div>
        </div>
      </li>
    {% endfor %}
  </ol>
</section>

<div class="video-modal" id="pub-video-modal" hidden>
  <button class="video-modal__close" type="button" aria-label="Close">&times;</button>
  <div class="video-modal__frame" id="pub-video-frame"></div>
</div>

<script>
(function () {
  var modal = document.getElementById('pub-video-modal');
  if (!modal) return;
  var frame = document.getElementById('pub-video-frame');
  function open(id, start) {
    var src = 'https://www.youtube-nocookie.com/embed/' + id + '?autoplay=1&rel=0' + (start ? '&start=' + start : '');
    frame.innerHTML = '<iframe src="' + src + '" title="Paper video" allow="autoplay; encrypted-media; picture-in-picture; fullscreen" allowfullscreen></iframe>';
    modal.hidden = false;
    requestAnimationFrame(function () { modal.classList.add('is-open'); });
    document.body.style.overflow = 'hidden';
  }
  function close() {
    modal.classList.remove('is-open');
    document.body.style.overflow = '';
    setTimeout(function () { modal.hidden = true; frame.innerHTML = ''; }, 200);
  }
  document.querySelectorAll('.pub__thumb--video').forEach(function (btn) {
    btn.addEventListener('click', function () {
      open(btn.getAttribute('data-video'), btn.getAttribute('data-start'));
    });
  });
  modal.querySelector('.video-modal__close').addEventListener('click', close);
  modal.addEventListener('click', function (e) { if (e.target === modal) close(); });
  document.addEventListener('keydown', function (e) { if (!modal.hidden && e.key === 'Escape') close(); });
})();
</script>
