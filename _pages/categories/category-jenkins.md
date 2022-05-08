---
title: "Jenkins"
layout: archive
permalink: categories/jenkins
author_profile: true
sidebar:
  nav: "docs"
---


{% assign posts = site.categories.jenkins %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}