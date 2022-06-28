---
published: true
title: "[Jekyll] minimal-mistakes에서 google search engine 등록하기"
date: 2022-06-27
last_modified_at: 2022-06-28T10:24:00
toc: true
toc_sticky: true
categories:
  - jekyll
tags:
  - jekyll
  - minimal-mistakes
  - google search engine
  - search_provider
  - search
---

## google search engine 등록 방법
Blog 내에서 검색 기능을 켤 수 있습니다. 해당 검색은 내 blog 내에서만 하는 것이며, 블로그 자료 검색 기능을 위해 사용 합니다. <br>

이를 제공하는 몇가지 solution이 있는 것 같은데, 저는 <b>Google CSE(Custom Search Engine)</b>을 이용해 검색 기능을 enable했습니다. <br>

## How to enable Google CSE

### Google CSE 등록하기
1. 아래 site에 접속
<https://programmablesearchengine.google.com/about/>

2. <b>"Get started"</b> 선택

3. <b>"검색할 사이트"</b>와 <b>"검색 엔진 이름"</b> 입력 및 <b>"언어"</b> 선택 후 <b>"만들기"</b> 선택<br>
<img src="https://user-images.githubusercontent.com/90759236/175883796-6e7cb003-cf3f-4ed5-97d7-50b0c2bb1741.png" style="border: 1px solid grey; max-width: 70%; height: auto;">

4. <b>"코드 가져오기"</b> 선택<br>
<img src="https://user-images.githubusercontent.com/90759236/175884310-c6dc5579-e452-42b8-b159-b6c814a3b786.png" style="border: 1px solid grey; max-width: 50%; height: auto;">

5. 아래 검은색 박스에 있는 코드 번호 copy<br>
<img src="https://user-images.githubusercontent.com/90759236/175884174-3dbee014-be80-4583-ba81-769c57090efd.png" style="border: 1px solid grey; max-width: 50%; height: auto;">

### <i>_config.yml</i> 수정
아래와 같이 _config.yml을 수정합니다.

```yml
search                   : true # true, false (default)
search_full_content      : # true, false (default)
search_provider          : "google" # lunr (default), algolia, google
algolia:
  application_id         : # YOUR_APPLICATION_ID
  index_name             : # YOUR_INDEX_NAME
  search_only_api_key    : # YOUR_SEARCH_ONLY_API_KEY
  powered_by             : # true (default), false
google:
  search_engine_id       : "MY SEARCH ENGINE ID" # YOUR_SEARCH_ENGINE_ID
  instant_search         : false # false (default), true
```

* search: true
* search_provider: "google"
* search_engine_id: 위 5번 과정에 있는 코드 번호 입력
<br>

## Reference
* minimal mistakes guide - <https://mmistakes.github.io/minimal-mistakes/docs/configuration/#google-custom-search-engine>