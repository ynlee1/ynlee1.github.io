---
published: true
title: "[Jekyll] Register Jekyll blog in google search engine"
last_modified_at: 2022-05-10T14:43:00
categories:
  - jekyll
tags:
  - google-search-console
  - jekyll
---

## 구글 검색 엔진에 Jekyll 블로그 등록

### 1. Google Search Console에 접속
[Google Searche Console](!https://search.google.com/search-console/about)에 접속해서 "시작하기"를 선택

### 2. 속성 유형 선택
아래 image처럼 GitHub blog URL을 "URL 접두어"에 입력 후 "계속"을 선택
<img src="https://user-images.githubusercontent.com/90759236/167544616-dc6d8194-49b6-484f-9e0d-5083f2d4699c.png" style="border: 1px solid grey">

### 3. 소유권 확인
1. html 파일을 download 후 Jekyll code 내 최상단 directory에 copy, commit & push를 진행
2. "확인" 버튼 클릭
<img src="https://user-images.githubusercontent.com/90759236/167544996-9390d32c-80d4-4794-a8b9-c37d3484d125.png" style="border: 1px solid grey">

### 4. 소유권 확인 완료 및 속성으로 이동
아래처럼 소유권 확인이 완료되면 "속성으로 이동" 선택, 이후 "시작" 선택
<img src="https://user-images.githubusercontent.com/90759236/167545168-e7300a97-7e0e-4015-8ada-59568767189e.png" style="border: 1px solid grey"><br>
<img src="https://user-images.githubusercontent.com/90759236/167545812-dcb5bd7a-a3b0-4547-ab16-fd91008e75cb.png" style="border: 1px solid grey">

### 5. Jekyll code 내에 sitemap.xml 추가
만약 Jekyll에서 자동으로 sitemap.xml을 생성했다면 따로 추가할 필요 없지만, 만약 sitemap.xml이 source code 최상단 directory에 존재하지 않는다면 아래 내용과 함께 파일 추가, commit & push.
```sh
---
layout: null
---
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  {% for post in site.posts %}
    <url>
      <loc>{{ site.url }}{{ post.url }}</loc>
      {% if post.lastmod == null %}
        <lastmod>{{ post.date | date_to_xmlschema }}</lastmod>
      {% else %}
        <lastmod>{{ post.lastmod | date_to_xmlschema }}</lastmod>
      {% endif %}

      {% if post.sitemap.changefreq == null %}
        <changefreq>weekly</changefreq>
      {% else %}
        <changefreq>{{ post.sitemap.changefreq }}</changefreq>
      {% endif %}

      {% if post.sitemap.priority == null %}
          <priority>0.5</priority>
      {% else %}
        <priority>{{ post.sitemap.priority }}</priority>
      {% endif %}

    </url>
  {% endfor %}
</urlset>
```

### 6. 색인 생성 요청
GitHub blog url과 사이트맵에 대한 색인 생성 요청
1. 좌측 메뉴에서 "URL 검사" 선택<br>
<img src="https://user-images.githubusercontent.com/90759236/167546245-98bc6876-9a7c-4a01-b721-9aef2374f86b.png" style="border: 1px solid grey">

2. GitHub blog url과 사이트맵에 대한 검색 및 색인 생성 요청
   1. https://{github account}.github.io
   2. https://{github account}.github.io/sitemap.xml
<img src="https://user-images.githubusercontent.com/90759236/167546503-e79c024e-53f2-4dfd-9dee-12e0e91a0087.png" style="border: 1px solid grey"><br>
<img src="https://user-images.githubusercontent.com/90759236/167552787-918f3da0-3d50-4c2f-8121-df4a06b505c6.png" style="border: 1px solid grey"><br>
<img src="https://user-images.githubusercontent.com/90759236/167553088-b208e9ae-8729-4120-abd5-1de7a878be1e.png" style="border: 1px solid grey"><br>
모든 setting 완료 후 URL이 Google 에 등록될 때까지 3일~7일(?) 걸리는 것 같다는 글을 구글링을 통해 확인했습니다. 추 후 내용 업데이트 예정입니다.

### 7. 새 사이트맵 추가
URL이 Google에 등록되면, 새 사이트맵을 추가<br>
(아직 제 blog가 Google에 등록되지 않았습니다. 등록 완료 후 해당 부분이 맞는지 업데이트 예정입니다.)
1. 좌측 메뉴에서 "Sitemap" 선택<br>
<img src="https://user-images.githubusercontent.com/90759236/167554859-bd17c5c4-1469-4588-87af-3542ab52c0cb.png" style="border: 1px solid grey">

2. 새 사이트맵 추가. sitemap.xml 입력 및 "제출" 선택<br>
<img src="https://user-images.githubusercontent.com/90759236/167554958-2e00b896-b230-4c4b-a229-a57f222b2dd2.png" style="border: 1px solid grey">


