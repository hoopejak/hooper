---
layout: single
title: "Artworks"
permalink: /artworks/
author_profile: true
---

{% comment %}
  This page displays a simple gallery of images contained in the `images/artworks` folder.
  Add your drawing files (e.g., JPG or PNG) to `images/artworks/` in the site root, and Jekyll will include them in the static files.
{% endcomment %}

<div class="art-gallery">
  {% for file in site.static_files %}
    {% if file.path contains 'images/artworks' %}
      <img src="{{ file.path | relative_url }}" alt="{{ file.name }}">
    {% endif %}
  {% endfor %}
</div>
