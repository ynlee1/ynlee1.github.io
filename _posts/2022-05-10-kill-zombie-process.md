---
published: true
title: "[Linux] How to kill zombie process"
last_modified_at: 2022-05-31T08:32:00
toc: true
toc_sticky: true
categories:
  - linux
tags:
  - linux
  - zombie-process
---

## Zombie process 확인 및 kill하는 방법

### Zombie process 확인
"top" command로 process 현황을 보면 zombie process가 존재하는지 확인 가능합니다.
<img src="https://user-images.githubusercontent.com/90759236/167793338-8092812b-6d91-44f6-a86e-02aca9b6ec90.png" style="border: 1px solid grey">

### Zombie process 찾기
```sh
ps -ef | grep defunct | grep -v grep
```

### Zombie process 수 확인
```sh
top -b -n 1 | grep zombie
```
혹은
```
ps -ef | grep defunct | grep -v grep | wc -l
```

### 모든 zombie process 죽이기
```sh
ps -ef | grep defunct | awk '{print $3}' | xargs kill -9
```

### Tip!. 강제로 zombie process 만들기
아래 코드는 zombie process를 만드는 간단한 C 코드로 child process가 종료되었지만 parent process가 handling을 할 수 없어, parent process가 종료되기 전까지 zombie process가 존재하는 코드입니다.
<script src="https://gist.github.com/ynlee1/841b136bbbe1f7677e3369237c77fffe.js"></script>

### Tip!. Defunct process, Orphan process란?
[코딩 초보의 블로그](https://coding-chobo.tistory.com/56)

