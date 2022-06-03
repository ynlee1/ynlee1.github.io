---
published: true
title: "[Jekyll] Minimal Mistake에서 category 추가하기"
date: 2022-06-03
last_modified_at: 2022-06-03T14:43:00
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
    
    ```yaml
    - title: "Language"
    children: 
      - title: "Markdown"
        url: categories/markdown
        category: "markdown"
      - title: "Python"
        url: categories/python
        category: "python"
    ```

    큰 title 내부에 작은 title 추가를 원하는 경우 `children`을 사용해서 구성할 수 있습니다. <br>해당 post에서는 <b>python</b> category 추가하는 것을 예로 진행합니다.

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


### 결과 화면
위에서 언급한 모든 flow를 완료하면, GitHub blog에서 아래처럼 새로운 category가 생성된 것을 확인할 수 있습니다. <br>
<img src="https://user-images.githubusercontent.com/90759236/171793964-81064925-f3ee-404d-9927-c1e42c74c4be.png" style="border: 1px solid grey; max-width: 70%; height: auto;"><br>



### 실제 post 작성 시 사용 예제
아래는 위에서 생성한 category를 이용해 새로 작성하는 post가 지정된 category 내부에 posting되도록 작성한 Front Matter입니다. <br>
`categories`를 보면 해당 post가 어떤 페이지에 속하는지 명시가 되어 있습니다. <br>

```md
---
published: true
title: "[Python] About Poetry"
date: 2022-06-03
last_modified_at: 2022-06-03T14:02:00
toc: true
toc_sticky: true
categories:
  - python
tags:
  - python
  - poetry
---
```
