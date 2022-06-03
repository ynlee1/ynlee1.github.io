---
published: true
title: "[Jekyll] Minimal Mistake에서 category 추가하기"
date: 2022-06-03
last_modified_at: 2022-06-03T14:04:00
toc: true
toc_sticky: true
categories:
  - jekyll
tags:
  - jekyll
  - minimal mistake
  - category
---

## Minimal Mistake 테마에서 category 추가
아래의 과정으로 Jekyll Minimal Mistake 테마에서 category를 추가할 수 있습니다.

1. <i>_data/navigation.yml</i>에서 추가하고자 하는 category 내용 추가<br>
    ```yml
    - title: "Language"
    children: 
    - title: "Markdown"
      url: categories/markdown
      category: "markdown"
    - title: "Python"
      url: categories/python
      category: "python"
    ```
    큰 title 내부에 작은 title 추가를 원하는 경우 `children`을 사용해서 구성할 수 있습니다. 해당 post에서는 <b>python</b> category 추가하는 것을 예로 진행합니다.

2. <i>_pages/categories</i>에 추가할 category 관련 md 파일 추가
    ```md
    ---
    title: "Python"
    layout: archive
    permalink: categories/python
    author_profile: true
    sidebar:
      nav: "docs"
    ---

    {% raw %}{%{% endraw %} assign posts = site.categories.categories %}
    {% raw %}{%{% endraw %} for post in posts %} {% raw %}{%{% endraw %} include archive-single.html type=page.entries_layout %} {% raw %}{%{% endraw %} endfor %}
    ```



