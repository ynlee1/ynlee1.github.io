---
title: "Windows"
layout: archive
permalink: categories/windows
author_profile: true
sidebar:
  nav: "docs"
---

{% assign posts = site.categories.windows %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}