---
published: true
title: "[Markdown] Insert image border in Markdown"
last_modified_at: 2022-05-09
categories:
  - markdown
tags:
  - markdown
  - HTML
  - border
---


## How to insert image border
GitHub README.md 기준, Markdown 방식의 URL 기반 image는 구글링에서 해본 것들을 다 해보았으나 모두 실패했고, 테스트 상 아래 방식(HTML)만 유일하게 동작하는 것 같습니다. <Br>

제 blog가 하얀색 바탕이라(기본 Jekyll라서) 이미지 구분이 잘 안되는 경우가 많은데, 아래 방식으로 이쁘지는 않지만 이미지 경계선을 추가해서 사용 중입니다.

### 기존 방식
```sh
![image](https://..)
```

### HTML border style을 이용한 경계선 추가
```sh
<img src="https://..." style="border: 1px solid grey">
```