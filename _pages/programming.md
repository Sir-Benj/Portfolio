---
layout: archive
permalink: /programming/
title: "Programming Projects"
author_profile: true
header:
    image: "/images/programming.png"
---

My major programming projects give a look at my coding abilities. 
Click on the links below to access the pages containing information on 
each project.

{% include base_path %}
{% include group-by-array collection=site.posts field="tags" %}
{% for tag in group_names %}
{% if tag == "python" %}
  {% assign posts = group_items[forloop.index0] %}
  <h2 id="{{ tag | slugify }}" class="archive__subtitle">Python</h2>
  {% for post in posts %}
    {% include archive-single.html %}
  {% endfor %}
{% endif %}
{% endfor %}


{% include base_path %}
{% include group-by-array collection=site.posts field="tags" %}
{% for tag in group_names %}
{% if tag == "c++" %}
  {% assign posts = group_items[forloop.index0] %}
  <h2 id="{{ tag | slugify }}" class="archive__subtitle">C++</h2>
  {% for post in posts %}
    {% include archive-single.html %}
  {% endfor %}
{% endif %}
{% endfor %}