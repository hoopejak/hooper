---
layout: simple
title: "Artworks"
permalink: /artworks/
---

{% include base_path %}
{% assign ordered_artworks = "artwork-01.jpg,artwork-13.jpg,artwork-09.jpeg,artwork-14.jpg,artwork-02.jpg,artwork-15.jpg,artwork-03.jpg,artwork-16.jpg,artwork-11.jpeg,artwork-17.jpg,artwork-04.jpg,artwork-18.jpg,artwork-06.jpg,artwork-19.jpg,artwork-10.jpeg,artwork-20.jpg,artwork-05.jpg,artwork-21.jpg,artwork-08.jpg,artwork-22.jpg,artwork-07.jpg,artwork-12.jpg" | split: "," %}

<section class="simple-page-heading">
  <h1>Artworks</h1>
  <p>A selection of drawings and visual studies.</p>
</section>

<section class="simple-gallery" aria-label="Artwork gallery">
  {% assign artwork_index = 0 %}
  {% for artwork_name in ordered_artworks %}
    {% assign artwork_path = '/images/artworks/' | append: artwork_name %}
    {% for file in site.static_files %}
      {% if file.path == artwork_path %}
        {% assign artwork_index = artwork_index | plus: 1 %}
        <figure class="simple-gallery__item">
          <a href="{{ file.path | prepend: base_path }}" target="_blank" rel="noopener noreferrer">
            <img src="{{ file.path | prepend: base_path }}" alt="Artwork {{ artwork_index }}" loading="lazy">
          </a>
        </figure>
      {% endif %}
    {% endfor %}
  {% endfor %}
</section>
