---
layout: archive
permalink: /mobiledev/
title: "Mobile Development Posts by Tags"
author_profile: true
header:
    image: "/images/flutter/mobile_dev.jpg"
---


{% include group-by-array collection=site.posts field="tags" %}

<!-- {% for tag in group_names %} -->
  {% assign posts = group_items[forloop.index0] %}
  <h2 id="{{ tag | slugify }}" class="archive__subtitle">{{ tag }}</h2>
  {% for post in posts %}
    {% include archive-single.html %}
  {% endfor %}
<!-- {% endfor %} -->