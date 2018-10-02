---
layout: archive
permalink: /unity&blender/
title: "Unity and Blender Projects"
author_profile: true
header:
    image: "/images/model.png"
---

*intro*

# Unity Projects

{% include base_path %}
{% include group-by-array collection=site.posts field="tags" %}

{% for tag in group_names %}
{% if tag == "unity" %}
  {% assign posts = group_items[forloop.index0] %}
  <h2 id="{{ tag | slugify }}" class="archive__subtitle">{{ tag }}</h2>
  {% for post in posts %}
    {% include archive-single.html %}
  {% endfor %}
{% endif %}
{% endfor %}

*To do: insert first project here*

# Blender Projects

{% include base_path %}
{% include group-by-array collection=site.posts field="tags" %}

{% for tag in group_names %}
{% if tag == "blender" %}
  {% assign posts = group_items[forloop.index0] %}
  <h2 id="{{ tag | slugify }}" class="archive__subtitle">{{ tag }}</h2>
  {% for post in posts %}
    {% include archive-single.html %}
  {% endfor %}
{% endif %}
{% endfor %}

*To do: insert modelling and animation here*