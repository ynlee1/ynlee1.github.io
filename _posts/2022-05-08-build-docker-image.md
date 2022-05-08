---
published: true
title: "How to build docker image"
last_modified_at: 2022-05-08
categories:
  - docker
tags:
  - docker
---

## Docker build
Docker image file 생성
```sh
docker build --tag [repository name]:[tag] .
```
  - -t, --tag: 새로 생성할 image의 name을 지정
  - 마지막의 점(.)은 Dockerfile 위치를 경로로 지정. 파일 이름이 Dockerfile이 아닌 경우 --file(-f) 옵션을 사용해서 파일 이름을 지정.
  <br><br>

## 생성한 Docker image를 사용해 Container 생성 및 실행
```sh
docker run --rm [repository name]:[tag]
```
  - --name: Container에 할당할 이름
  - -p, --publish: host에 container port 5000번 publish
  - -d, --detech: daemon으로 실행(background)
  - -i, --iterative: 표준 입력(stdin)을 활성화하고, container와 연결되어 있지 않더라도 표준 입력 유지
  - -t, --tty: TTY 모드 사용(for bash)
  - -v, --volume: Data volume을 설정, Host와 container의 directory를 연결하여, file을 container에 저장하지 않고 host에 바로 저장(mount)
  - -u, --user: Container가 실행될 linux user account 이름 또는 UID를 설정
    - --user root
  - -h, --hostname: Container의 host name을 설정
  - -w, --workdir: Container 안의 proces가 실행될 directory를 설정
  - -a, --attach: Container에 stdin, stdout, stderr를 연결
  - -e, --env: Container 내에서 사용할 환경 변수를 설정, 보통 설정 값이나 비밀번호 전달 시 사용
  - -c, --cpu-shares: CPU resource 분배 설정, 기본 값은 1024
  - -m, --memory: 메모리 한계를 설정, 단위는 b, k, m, g를 사용할 수 있음
    - --memory="1000000b"
  - --privileged: Container 안에서 host의 linux kernel 기능(Capability)을 모두 사용
  - --rm: Container 내부 process 종료 시 container 자동 제거
  - --link: Container끼리 연결
    - --link="db:db"
  - --gpus: Container에서 host의 NVIDIA GPU를 사용할 수 있도록 설정. Docker 19.03.5 version 이상 제공
  - --security-opt: SELinux, AppArmor 옵션을 설정
  - --restart=always: 부팅 시 자동 시작<br><br>