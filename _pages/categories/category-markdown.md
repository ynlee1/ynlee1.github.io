---
title: "Markdown"
layout: archive
permalink: categories/markdown
author_profile: true
sidebar:
  nav: "docs"
---


{% assign posts = site.categories.markdown %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}