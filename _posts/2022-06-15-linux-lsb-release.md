---
published: true
title: "[Linux] lsb_release command"
date: 2022-06-15
last_modified_at: 2022-06-15T08:33:00
toc: true
toc_sticky: true
categories:
  - linux
tags:
  - linux
  - lsb_release
---

## Linux 배포판 버전 확인 방법 - <i>lsb_release</i>
<i>lsb_release</i>는 리눅스 배포판 version을 확인하기 위한 간편한 command입니다.

### What is LSB?
LSB는 Linux Standard Base의 약자로, Linux 재단의 조직 구조에 속하는 일부 linux 배포판들의 공동 프로젝트로서, linux OS에 쓰이는 file system 계층을 포함한 software system 구조를 표준화하는 것이 목적이라고 합니다. (출처: wikipedia) <br>

### lsb_release
<i>lsb_release</i>는 위에서 설명한 Linux 배포판 version을 확인하기 위한 command입니다. 사용방법은 아래와 같습니다. <br>

```sh
$ lsb_release [option]
```

해당 command의 option은 아래와 같습니다. Ubuntu 20.04 기준입니다.
| option | description |
| :--------------: | :---------------------------------------------------------- |
| -a, --all | print all information |
| -s, --kernel-name | print the kernel name |
| -n, --nodename | print the network node hostname |
| -r, --kernel-release | print the kernel release |
| -v, --kernel-version | print the kernel version |
| -m, --machine | print the machine hardware name |
| -p, --processor | print the processor type (non-portable) |
| -i, --hardware-platform | print the hardware platform (non-portable) |
| -o, --operating-system | print the operating system |
| --help |  display this help and exit |
| --version | output version information and exit |

### 사용 예제
저는 보통 "-a" option만 사용합니다. Kernel version을 알고 싶은 경우에는 <i>uname</i> command를 사용합니다. <br>

```sh
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:        20.04
Codename:       focal
```

### No LSB modules are available
위와 같은 error? warning? 문구는 lsb module을 설치해줘야 없어집니다. 저는 딱히 필요없어서 설치하지 않았습니다. <br>
```sh
$ sudo apt-get install lsb
```


## Reference
[LSB 정의 - wikipedia](https://ko.wikipedia.org/wiki/%EB%A6%AC%EB%88%85%EC%8A%A4_%EA%B8%B0%EB%B3%B8_%EA%B7%9C%EA%B2%A9)