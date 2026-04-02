---
permalink: /
title: "Jake Hooper"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

{% include base_path %}
{% assign ordered_artworks = "artwork-01.jpg,artwork-13.jpg,artwork-09.jpeg,artwork-14.jpg,artwork-02.jpg,artwork-15.jpg,artwork-03.jpg,artwork-16.jpg,artwork-11.jpeg,artwork-17.jpg,artwork-04.jpg,artwork-18.jpg,artwork-06.jpg,artwork-19.jpg,artwork-10.jpeg,artwork-20.jpg,artwork-05.jpg,artwork-21.jpg,artwork-08.jpg,artwork-22.jpg,artwork-07.jpg,artwork-12.jpg" | split: "," %}

<section class="home-hero">
  <p class="home-hero__lead">I'm a first year doctoral student in cognitive systems neuroscience at the University of Oregon, advised by <a href="https://serenolab.uoregon.edu">Dr. Margaret Sereno</a>. My work focuses on visual perception, aesthetic experience, self models, and altered states of consciousness. I am also a Fellow of the <a href="https://www.activeinference.institute/">Active Inference Institute</a>, where I contribute to interdisciplinary conversations in theoretical neuroscience. Previously, I worked as a clinical research coordinator in the <a href="https://medschool.cuanschutz.edu/psychiatry/research/faculty-labs/chaos-lab">CHAOS Lab</a> housed within the Department of Psychiatry at the University of Colorado Anschutz. There, I managed several clinical trials on substance use and cognitive impairment, with a focus on cannabis, and helped expand research into the emerging field of psychedelics.</p>
</section>

<section class="home-section">
  <h2>Research</h2>
  <p>My research connects neuroscience, psychology, complexity, and aesthetics. I am especially interested in how perception becomes meaningful experience, and why some encounters with art, nature, or altered states feel transformative.</p>
  <div class="home-grid">
    <div class="home-card">
      <h3>Aesthetic experience</h3>
      <p>I approach aesthetic experience through hierarchical predictive coding, asking how the brain interprets particular sets of stimulus features as emotionally meaningful.</p>
    </div>
    <div class="home-card">
      <h3>Fractal complexity</h3>
      <p>Fractals offer a scalable, quantifiable bridge between natural patterns, visual art, neural dynamics, and psychedelic visual phenomenology.</p>
    </div>
    <div class="home-card">
      <h3>Psychedelics and consciousness</h3>
      <p>I am interested in how altered states of consciousness can clarify mechanisms of perception, cognition, and aesthetic experience.</p>
    </div>
    <div class="home-card">
      <h3>Active inference</h3>
      <p>My involvement with the <a href="https://www.activeinference.institute/">Active Inference Institute</a> complements my interest in hierarchical predictive coding and questions about how brains generate perception, meaning, and models of self and world.</p>
    </div>
  </div>
</section>

<section class="home-section home-section--compact">
  <div class="home-section__header">
    <h2>Selected Publications</h2>
    <a href="{{ base_path }}/publications/">See all</a>
  </div>
  <div class="home-list">
    {% assign featured_publications = "/publication/2025-psilocybin-outside-the-clinic,/publication/2025-neuroaesthetics-of-the-psychedelic-state" | split: "," %}
    {% for featured_url in featured_publications %}
      {% for post in site.publications %}
        {% if post.url == featured_url %}
          <article class="home-list__item">
            <h3><a href="{{ base_path }}{{ post.url }}">{{ post.title }}</a></h3>
            <p class="home-list__meta">{{ post.venue }}, {{ post.date | date: "%Y" }}</p>
            {% if post.excerpt %}<p>{{ post.excerpt }}</p>{% endif %}
          </article>
        {% endif %}
      {% endfor %}
    {% endfor %}
  </div>
</section>

<section class="home-section">
  <div class="home-section__header">
    <h2>Visual Work</h2>
    <a href="{{ base_path }}/artworks/">See gallery</a>
  </div>
  <p>Alongside my research, I also make visual artwork.</p>
  <div class="home-art-preview">
    {% assign preview_count = 0 %}
    {% for artwork_name in ordered_artworks %}
      {% assign artwork_path = '/images/artworks/' | append: artwork_name %}
      {% for file in site.static_files %}
        {% if file.path == artwork_path and preview_count < 3 %}
          {% assign preview_count = preview_count | plus: 1 %}
          <a class="home-art-preview__item" href="{{ base_path }}/artworks/">
            <img src="{{ file.path | prepend: base_path }}" alt="Artwork preview {{ preview_count }}" loading="lazy">
          </a>
        {% endif %}
      {% endfor %}
    {% endfor %}
  </div>
</section>
