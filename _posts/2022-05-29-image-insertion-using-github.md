---
published: true
title: "[Markdown] 이미지를 markdown에 간단하게 추가하는 방법"
last_modified_at: 2022-05-31T08:33:00
toc: true
toc_sticky: true
categories:
  - markdown
tags:
  - markdown
  - github
  - image
  - github discussion
  - github issues
---

## GitHub를 이용해 이미지를 markdown에 간단하게 추가하는 방법
Markdown 작성 시 GitHub의 discussion이나 issue를 이용해 간단하게 이미지를 추가할 수 있습니다.<br>


1. 이미지 캡처
본인이 편한 방법대로 이미지를 캡처합니다.<br>
저는 예제로 제 blog 화면을 캡처했습니다.<br>
이미지 캡처에 관련된 내용은 아래 post 참조하시기 바랍니다.<br>

---
{% assign posts = site.categories.windows %}
{% for post in posts %}
  {% if post.title contains 'Windows 스크린샷' %}
    {% include archive-single.html type=page.entries_layout %}
  {% endif %} 
{% endfor %}

---
2. GitHub discussion이나 issue 페이지로 이동
본인이 관리하고 있거나 가지고 있는 GitHub의 discussion 페이지나 issue 페이지로 이동합니다.<br>
새로운 issue나 discussion을 open합니다.<br>
<img src="https://user-images.githubusercontent.com/90759236/170876567-44ea0996-98da-41be-81c8-90a1d564e689.png" style="border: 1px solid grey; max-width: 70%; height: auto;"><br>

3. 캡처한 이미지를 issue나 discussion 글에 붙여넣기(ctrl + v)하면 markdown 형식의 code(?)가 나옵니다.<br>
<img src="https://user-images.githubusercontent.com/90759236/170876642-e2fb3c27-94e6-43d4-8182-91a82f42b184.png" style="border: 1px solid grey; max-width: 70%; height: auto;"><br>

4. 해당 code를 그대로 markdown에 작성하면 이미지가 삽입됩니다.
Markdown에서 image 삽입에 경계선을 넣는 방법은 아래의 post를 참조하시기 바랍니다!

---
{% assign posts = site.categories.markdown %}
{% for post in posts %}
  {% if post.title contains 'Insert image border in Markdown' %}
    {% include archive-single.html type=page.entries_layout %}
  {% endif %} 
{% endfor %}

---
{{ site.baseurl }}{% post_url 2022-05-09-insert-image-border-in-markdown %}