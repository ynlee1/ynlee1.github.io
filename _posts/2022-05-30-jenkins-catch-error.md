---
published: true
title: "[Jenkins] Pipeline에서 stage faild이 발생해도 다음 stage로 넘어가도록 하는 방법"
date: 2022-05-30
last_modified_at: 2022-06-14T16:42:00
toc: true
toc_stricky: true
categories:
  - jenkins
tags:
  - jenkins
  - pipeline
  - catchError
---

## catchError
<i>catchError</i>는 stage에서 exception이 발생하면 build를 failure로 표시하지만 <i>catchError</i> 단계 다음 command에서 pipeline을 계속 실행시켜 줍니다. <br>즉, 특정 stage에서 fail이 발생해도 다음 stage로 넘어갈 수 있도록 해주는 pipeline step입니다.<br>

### Exception 발생 시 구성할 수 있는 catchError 동작
1. Message 출력 (log message)
2. 'failure' 이외의 다른 build 결과를 설정
     - example: 'unstable'
3. 'failure' 이외의 다른 stage 결과로 설정
4. Build를 중단하는데 사용되는 특정 종류의 exception을 무시
     - Build를 수동으로 중단시 발생하는 exception
     - timeout에 의해 발생하는 exception

### catchError 기본 문법
catchError 기본 문법은 아래와 같습니다.<br>
```groovy
catchError(message: 'message', buildResult: 'STABLE'|'FAILURE'|'SUCCESS'|..., stageResult: 'STABLE'|'FAILURE'|'SUCCESS'|..., catchInterruptions: true|false) {
  sh 'action'
}
```
* message: Exception 발생 시 console에 기록될 message입니다.
* message field는 문서상 optional은 아니나, test상 없어도 무방한 것 같습니다.
* catchInterruptions의 경우 optional이고, default값은 true입니다.
* catchInterruptions가 true인 경우 해당 exception(build 중단 및 timeout)이 이 stage에서 catch 및 처리 됩니다.

## Example
아래 post 예제에서 <i>catchError</i>를 추가한 간단한 예제입니다. <br>
stage 단계에서 exception 발생 시 stage 결과는 failure로 보이지만, 전체 pipeline result에는 영향이 없는 code입니다. <br>

---
{% assign posts = site.categories.jenkins %}
{% for post in posts %}
  {% if post.title contains 'Dynamic stages in Jenkins pipeline' %}
    {% include linked-post.html type=page.entries_layout %}
  {% endif %} 
{% endfor %}

---
<script src="https://gist.github.com/ynlee1/00c110cd64e8afc54215b1f8eb8e7693.js"></script>


## Reference
[Jenkins Guide Doc](https://www.jenkins.io/doc/pipeline/steps/workflow-basic-steps/)
