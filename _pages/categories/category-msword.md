---
title: "Word"
layout: archive
permalink: categories/msword
author_profile: true
sidebar:
  nav: "docs"
---

{% assign posts = site.categories.msword %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}