---
title: "Python"
layout: archive
permalink: categories/python
author_profile: true
sidebar:
  nav: "docs"
---


{% assign posts = site.categories.python %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}