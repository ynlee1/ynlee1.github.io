---
published: true
title: "[Jenkins] 'post' section in Jenkins pipeline"
date: 2022-06-07
last_modified_at: 2022-06-08T00:34:00
toc: true
toc_sticky: true
categories:
  - jenkins
tags:
  - jenkins
  - pipeline
  - post
  - post action
---

## <i>'post'</i> section
Jenkins pipeline에서 <i>'post'</i> section은 pipeline 동작 완료 후 실행되는 하나 이상의 추가 단계를 정의할 때 사용합니다. <br>
예를 들어 모든 pipeline stage가 완료 후 수행 결과를 noti할 때 (email이나 Slack, MS Teams 등으로 전송) <i>'post'</i> section을 사용하면 손쉽게 구현할 수 있습니다. <br>

### <i>'post'</i> section의 상태 값
<i>'post'</i> section은 총 10개의 상태 값을 가지고 있습니다. <br>
Pipeline 완료 상태에 따라 해당 상태 값들이 결정되며, 이 완료 상태를 보고 <i>'post'</i> section을 수행할지 말지를 결정하도록 구현할 수 있습니다. <br>

| post-condition | description |
| :---------------------: | :----------------------------------------------------------- |
| always | Pipeline 실행 완료 상태와 관계 없이 <i>'post'</i> section을 수행 |
| changed | 이전 실행 완료 상태와 다를 때에만 <i>'post'</i> section을 수행 |
| fixed | 현재 pipeline 실행 완료 상태가 'success'이고, 이전 실행 완료 상태가 'unstable'이거나 'failure'인 경우에만 <i>'post'</i> section을 수행 |
| regression | 현재 pipeline 실행 완료 상태가 'failure'나 'unstable'이고, 이전 실행 완료 상태가 'success'인 경우에만 <i>'post'</i> section을 수행 |
| aborted | 현재 pipeline의 실행 완료 상태가 'aborted'(Web에서 봤을 때 회색, 강제 종료의 경우)인 경우에만 <i>'post'</i> section을 수행 |
| failure | 현재 pipeline의 실행 완료 상태가 'failure'인 경우에만 <i>'post'</i> section을 수행 |
| success | 현재 pipeline의 실행 완료 상태가 'success'인 경우에만 <i>'post'</i> section을 수행 |
| unstable | 현재 pipeline의 실행 완료 상태가 'unstable'(Web에서 봤을 때 노란색, pipeline이 완료는 되었으나 warning등이 존재하는 경우)인 경우에만 <i>'post'</i> section을 수행 |
| unsuccessful | 현재 pipeline의 실행 완료 상태가 'success'가 <b>아닌</b> 경우에만 <i>'post'</i> section을 수행 |
| cleanup | Pipeline 실행 완료 상태와 상관 없이 위에서 언급한 다른 post condition이 평가 된 후 이 조건의 <i>'post'</i> section이 수행 |

<br>

### Example
아래는 간단한 예제입니다. 아래 post의 dynamic stage에 <i>'post'</i> section을 추가했습니다.

---
{% assign posts = site.categories.jenkins %}
{% for post in posts %}
  {% if post.title contains 'Dynamic stages in Jenkins pipeline' %}
    {% include archive-single.html type=page.entries_layout %}
  {% endif %} 
{% endfor %}
{% post_url 2022-05-23-jenkins-dynamic-stages %}

---
<script src="https://gist.github.com/ynlee1/0336a8e3f2ce2ed73d49d4d6cf23de3d.js"></script>
