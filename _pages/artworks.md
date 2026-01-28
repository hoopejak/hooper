---
layout: single
title: "Artworks"
permalink: /artworks/
author_profile: true
---

{% include base_path %}

{% assign artworks = site.static_files | where_exp: "f", "f.path contains '/images/artworks/'" %}

{%- comment -%}
Optional: if filenames begin with YYYY-MM-DD_ or 001_, sorting will be stable and meaningful.
{%- endcomment -%}
{% assign artworks = artworks | sort: "name" | reverse %}

<div class="art-gallery" role="list">
  {% for file in artworks %}
    {% assign ext = file.extname | downcase %}
    {% if ext == ".jpg" or ext == ".jpeg" or ext == ".png" or ext == ".webp" or ext == ".gif" %}

      {% assign stem = file.name | split: "." | first %}
      {% assign caption = stem | replace: "-", " " | replace: "_", " " %}

      <figure class="art-item" role="listitem">
        <a href="{{ file.path | prepend: base_path }}">
          <img
            src="{{ file.path | prepend: base_path }}"
            alt="{{ caption | escape }}"
            loading="lazy"
            decoding="async"
          >
        </a>
        <figcaption class="art-caption">{{ caption }}</figcaption>
      </figure>

    {% endif %}
  {% endfor %}
</div>

