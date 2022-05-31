---
published: true
title: "[Linux] Get memory Information"
last_modified_at: 2022-05-31T14:01:00
toc: true
toc_sticky: true
categories:
  - linux
tags:
  - linux
  - free
  - meminfo
---

## Memory 정보를 얻을 수 있는 command

### <u>free</u>
가장 쉽게 memory 정보를 얻을 수 있는 command입니다. <br>
일반적으로 새로운 application을 실행하기 위해 사용할 수 있는 memory 양을 확인하기 위해 많이 쓰이며, <br>
모든 정보들은 <i>/proc/meminfo</i>의 정보들을 이용해 구성된 값입니다. <br>
아무 option 없이 실행했을 때에는 kb 단위 값들을 보여 줍니다. <br><br>

```sh
$ free
```
![image](https://user-images.githubusercontent.com/90759236/171095851-f008f52f-4371-4101-845d-1a27ddbbb506.png) <br>

아래는 각 필드의 정의 입니다. <br>

|` field `|` description `|
| :-----: | :----------------------------------------------------------- |
| total | 설치된 총 memory |
| used | 실행중인 process들이 사용하고 있는 memory ( total - free - buff/cache ) |
| free | 사용하지 않는 memory |
| shared | 여러 process간 공유 memory |
| buffers | Process가 memory를 필요로 할 때 buffer로 할당하기 위해 OS가 예약한 memory |
| cached | RAM에 저장된 최근 사용한 파일 |
| buff/cache | Buffers + Cache |
| available | Swapping 없이 새 응용 프로그램을 시작하는 데 사용할 수 있는 메모리 양(추정값) |

<li><i>Swapping은 memory가 부족할 경우 하드 디스크의 일부 공간을 활용하여 작업을 도와주는 것을 말하며, memory 공간 부족 방지를 위해 사용합니다.</i></li><br><br>

`free` command의 option은 아래와 같습니다. <br>

```sh
$ free -help
```

<img src="https://user-images.githubusercontent.com/90759236/171094381-ac1a69e9-3ac0-45bb-b2e1-f28f95aa7cd2.png"> <br>


### <u>/proc/meminfo</u>
`cat` command와 보통 함께 쓰며, 사용 가능한 memory와 사용된 memory 양을 보고하는 가상 file입니다. <br>
시스템의 메모리 사용량과 kernel에서 사용하는 buffer 및 공유 memory에 대한 <b>실시간 정보</b>를 보여주며, 출력 방식은 architecture나 OS마다 조금 씩 다릅니다. <br>

```sh
$ cat /proc/meminfo
```

<img src="https://user-images.githubusercontent.com/90759236/171094213-d2ac3569-9174-4fbc-b148-0dc17c050bc2.png"> <br>


## Reference
<https://phoenixnap.com/kb/linux-commands-check-memory-usage>