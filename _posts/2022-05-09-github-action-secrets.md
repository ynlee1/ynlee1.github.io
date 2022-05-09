---
published: true
title: "[GitHub] GitHub Actions secrets"
last_modified_at: 2022-05-09T12:54
categories:
  - github
tags:
  - github
  - action-secrets
---

## How to register new repository secret
GitHub Action 사용 시 secret이 필요한 경우가 많습니다(예를 들면 clone action). Action을 등록하는 방식에는 repository secret과 organization secret이 있는데, 해당 글에서는 repository secret을 등록하는 방법에 대해 설명하겠습니다.

### 1. Secret이 필요한 repository에 들어가 "settings"를 클릭
<img src="https://user-images.githubusercontent.com/90759236/167338413-16bdfe8a-954f-44d9-bae7-1e45ff6aa894.png" style="border: 1px solid grey">

### 2. "Security-->Secrets-->Actions"를 클릭
<img src="https://user-images.githubusercontent.com/90759236/167338458-6357784f-18cf-45a0-8f16-2ea99ee38ed5.png" style="border: 1px solid grey">

### 3. Action secrets 창에서 New repository secret 클릭
<img src="https://user-images.githubusercontent.com/90759236/167338495-62d746a3-0246-48cd-b9ab-0e9c7df4dbc0.png" style="border: 1px solid grey">

### 4. Secret Name과 Value 입력 후 "Add secret" 클릭
Secret Name은 원하는 이름을 입력하면 되며, Value는 PAT(Personal Access token)입니다.<br>
<img src="https://user-images.githubusercontent.com/90759236/167338507-de76ce81-a158-41a3-9f0b-acdfb8961ad1.png" style="border: 1px solid grey">
<br>PAT 관련 내용은 아래 글을 참조하시기 바랍니다.<br>

<ul>
  {% assign posts = site.categories.github %}
  {% for post in posts %}
    {% if post.title contains 'Token' %}
      <li>{% include archive-single.html type=page.entries_layout %}</li>
    {% endif %} 
  {% endfor %}
</ul>

### 5. 실제 code에서 위에서 지정한 secret name을 사용
아래는 Secret Name을 ACTION_AUTH로 지정한 예제입니다. {secrets.ACTION_AUTH} 양 옆 '는 제거하셔야 합니다.
```sh
- name: Clone PR branch
  uses: actions/checkout@v2
  with:
    token: ${'{ secrets.ACTION_AUTH }'}
    fetch-depth: 1
```