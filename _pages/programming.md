---
layout: archive
permalink: /programming/
title: "Programming Projects"
author_profile: true
header:
    image: "/images/reflections.png"
---

{% include base_path %}
{% include group-by-array collection=site.posts field="tags" %}

*intro*

*add links to click that take you directly to the project on this page*

# Python

{% for tag in group_names %}
{% if tag == "python" %}
  {% assign posts = group_items[forloop.index0] %}
  <h2 id="{{ tag | slugify }}" class="archive__subtitle">{{ tag }}</h2>
  {% for post in posts %}
    {% include archive-single.html %}
  {% endfor %}
{% endif %}
{% endfor %}

*talk about Army of One, insert code, critique code*

# C++

{% for tag in group_names %}
{% if tag == "c++" %}
  {% assign posts = group_items[forloop.index0] %}
  <h2 id="{{ tag | slugify }}" class="archive__subtitle">{{ tag }}</h2>
  {% for post in posts %}
    {% include archive-single.html %}
  {% endfor %}
{% endif %}
{% endfor %}

*talk about It's High Noon!, insert code, critique code*