---
layout: single
title: "Artworks"
permalink: /artworks/
author_profile: true
---

{% comment %}
  This page displays a simple gallery of images contained in the images/artworks folder.
  Add your drawing files (e.g., JPG or PNG) to images/artworks/ in the site root.
{% endcomment %}

{% include base_path %}

<div class="artworks-intro">
  <p>This page collects a selection of my visual work. Click any image to view it at full size.</p>
</div>

<div class="art-gallery" role="list">
  {% assign artwork_index = 0 %}
  {% for file in site.static_files %}
    {% if file.path contains 'images/artworks' %}
      {% assign artwork_index = artwork_index | plus: 1 %}
      <figure class="art-gallery__item" role="listitem">
        <a href="{{ file.path | prepend: base_path }}" target="_blank" rel="noopener noreferrer">
          <img
            src="{{ file.path | prepend: base_path }}"
            alt="Artwork {{ artwork_index }}"
            loading="lazy">
        </a>
      </figure>
    {% endif %}
  {% endfor %}
</div>
