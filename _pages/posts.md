---
layout: archive
title: "Blogs"
permalink: /posts/
author_profile: true
---

{% include base_path %}

{% for post in site.posts reversed %}
  {% include archive-single.html %}
{% endfor %}
