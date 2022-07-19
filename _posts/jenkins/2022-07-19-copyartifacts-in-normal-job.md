---
published: true
title: "[Jenkins] Jenkins job configure에서 copyArtifacts 사용 방법"
date: 2022-07-19
last_modified_at: 2022-07-19T16:43:00
toc: true
toc_sticky: true
categories:
  - jenkins
tags:
  - jenkins
  - copyArtifacts
  - job configure
---

* <b>작성일</b>: 2022/07/19
* <b>관련 blog</b>: <u>Pipeline에서 copyArtifacts 생성하기</u>

---
{% assign posts = site.categories.github %}
{% for post in posts %}
  {% if post.title contains 'Draft Pull Request' %}
    {% include linked-post.html type=page.entries_layout %}
  {% endif %} 
{% endfor %}

---

## Jenkins job 내부에서 copyArtifacts 사용하기

위 post에서는 pipeline script 내부에서 copyArtifacts를 사용하는 방법을 설명했습니다. <br>
해당 post에서는 일반 Jenkins Job 내부에서 copyArtifacts 설정 방법을 설명합니다. <br>
<br>

1. "<b>Build</b>" 단계에서 "<b>Add build step</b>" -> "<b>Copy artifacts from another project</b>" 선택
<img src="https://user-images.githubusercontent.com/90759236/179697059-3fc021c6-2a5f-4a97-84bf-687fe7ffe694.png" style="border: 1px solid grey; max-width: 50%; height: auto;"><br>

2. Copy할 project의 "Permission to Copy Artifact" 활성화<br>
Artifact를 가져올 project의 job configuration에서 "Permission to Copy Artifact"를 활성화<br>
<u>(저는 보통 wildcard ("*")로 셋팅합니다.)</u><br>
<img src="https://user-images.githubusercontent.com/90759236/179703738-58a3b1e9-37de-407f-ad04-9abff11a71b1.png" style="border: 1px solid grey; max-width: 50%; height: auto;"><br>

3. 각 영역에 원하는 값 설정<br>
<img src="https://user-images.githubusercontent.com/90759236/179697775-70ce9fd1-56c3-43c2-8797-0cdb27228787.png" style="border: 1px solid grey; max-width: 90%; height: auto;"><br>

   * <b>Project name</b>: Copy할 project name
   * <b>Which build</b>: 위 project의 어떤 build에서 가져올 것인지 선택
   * <b>Artifacts to copy</b>: Copy할 artifact의 상대 경로. 공백으로 두면 모든 artifact가 복사되며, wildcard를 사용할 수 있음. 쉼표를 통해 여러 항목 구분 가능
   * <b>Artifacts not to copy</b>: Exclude할 path나 pattern
   * <b>Target directory</b>: 복사한 artifact를 저장할 target path
   * <b>Parameter filters</b>: 특정 매개변수 또는 빌드 변수와 일치하는 build만 선택하도록 filtering할 때 사용
   * <b>Flatten directories</b>: 복사할 artifact의 directory 구조는 copy해오지 않음
   * <b>Optional</b>: copyArtifacts애서 실패가 발생하더라도 step 실패가 발생하지 않음
   * <b>Fingerprint Artifacts</b>: artifact의 MD5 checksum을 기록, 빌드를 추적하는데 사용
