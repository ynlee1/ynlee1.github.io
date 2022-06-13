---
published: true
title: "[Linux] 실행 파일 경로를 확인하는 방법(which/whereis)"
date: 2022-06-07
last_modified_at: 2022-06-13T09:20:00
toc: true
toc_sticky: true
categories:
  - linux
tags:
  - linux
  - which
  - whereis
  - file
  - location
---

## Linux의 실행 파일 경로를 확인하는 방법
Linux에서 python을 실행할 때 우리는 당연하게도 <i>python</i>이라는 명령어를 CLI창에 입력합니다. <br>
일반적으로 사용하는 <i>python</i>같은 linux command는 보통 환경변수로 잡혀 있고, 실제 파일(binary나 script) 위치는 다른 곳에 있습니다. <br>
<i>which</i>와 <i>whereis</i> command는 실제 파일 위치를 찾아서 알려주는 command입니다.<br><br>

### which
<i>which</i> command는 환경 변수(environment variable)인 <b>$PATH</b>를 기초로 경로를 검색 및 출력해줍니다.<br>
만약 환경 변수 <b>$PATH</b> 내에 입력한 command가 존재하지 않는다면, 해당 command의 경로는 출력되지 않습니다.<br>

- Usage
  ```sh
  which (option) [command/file name]
  ```
- Option
  | Option | Description |
  | :--------: | :------------------------------------------- |
  | -a | 입력한 command나 file name과 일치하는 모든 경로를 출력 |
- Example
  ```sh
  $ which ls
  /usr/bin/ls
  ```

  ```sh
  $ which -a ls
  /usr/bin/ls
  /bin/ls
  ```
<br>

### whereis
<i>whereis</i> command는 standard Linux 경로(/bin, /etc, /usr 등)와 환경 변수 <b>$PATH</b> 및 $MANPATH의 내부 목록을 검색합니다.<br>
또한 <i>whereis</i>는 실행 파일 뿐만 아니라 source file, menual까지 대상으로 합니다. <br>

- Usage
  ```sh
  whereis (option) [command/file name]
  ```
- Option
  | Option | Description |
  | :--------: | :------------------------------------------- |
  | -b | binary를 search |
  | -m | manual을 search |
  | -s | soruce file을 search |
  | -u | 특정 파일을 제외 |
  | -B <u>list</u> | binary file의 위치를 제한(각 directory는 공백으로 구분), -f option과 함께 사용 |
  | -M <u>list</u> | menual page의 위치를 제한(각 directory는 공백으로 구분), -f option과 함께 사용 |
  | -S <u>list</u> | 원본 file의 위치를 제한(각 directory는 공백으로 구분), -f option과 함께 사용 |
  | -f | -B, -M, -S option에 directory를 지정한 다음, 이 option에서 file명을 지정 |
  | -l | file을 조회하는 경로(디렉토리) 목록을 출력 |
  | -v | version 정보 출력 |
- Example
  ```sh
  $ whereis python
  python: /usr/bin/python3.9 /usr/bin/python3.8-config /usr/bin/python3.8 /usr/lib/python3.9 /usr/lib/python2.7 /usr/lib/python3.8 /etc/python3.9 /etc/python3.8 /usr/local/lib/python3.9 /usr/local/lib/python3.8 /usr/include/python3.8
  ```
