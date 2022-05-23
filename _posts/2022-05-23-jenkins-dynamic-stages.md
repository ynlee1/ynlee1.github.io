---
published: true
title: "[Jenkins] Dynamic stages in Jenkins pipeline"
last_modified_at: 2022-05-23T12:41:00
categories:
  - jenkins
tags:
  - jenkins
  - pipeline
  - dynamic-stages
---

## Jenkins pipeline에서 동작 stage 생성하기
Jenkins pipeline을 구성하다 보면, 각 stage를 하나씩 구성하는 것이 아닌, 단순 job trigger를 구성할 때도 있습니다. 이 때 stage를 하나씩 추가하는 것은 너무 비효율적이고 유지보수에도 좋지 않습니다. 이 때는 for문을 이용해서 동적으로 stage를 생성하도록 구성할 수 있습니다. <br>

<script src="https://gist.github.com/ynlee1/26c1eceffc53f232a734684189f17ef7.js"></script>