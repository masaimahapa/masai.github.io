---
layout: archive
permalink: /data-science/
title: "Data Science Posts by Tags"
author_profile: true
    image: "images/data.png"
---

{% include base_path %}
{% include group-by-array collection=site.posts field="tags" %}

{% for tag in group_names %}
    {% assign posts = group_items[forloop.index0] %}
    <h2 id="{{ tags | slugify }}" class="archive__subtitile">{{ tag }}</h2>
    {% for post in posts %}
        {% include archive-single.html %}
    {% endfor %}
{% endfor %}