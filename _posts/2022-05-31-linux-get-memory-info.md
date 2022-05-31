---
published: true
title: "[Linux] Get memory Information"
last_modified_at: 2022-05-31T10:42:00
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

```
$ free
              total        used        free      shared  buff/cache   available
Mem:       32887408     7040376     3945688     6588732    21901344    18786800
Swap:             0           0           0
```
<br>
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

<li><i>Swapping은 memory가 부족할 경우 하드 디스크의 일부 공간을 활용하여 작업을 도와주는 것을 말하며, memory 공간 부족 방지를 위해 사용합니다.</i><br><br>

`free` command의 option은 아래와 같습니다. <br>

```
$ free --h

Usage:
 free [options]

Options:
 -b, --bytes         show output in bytes
     --kilo          show output in kilobytes
     --mega          show output in megabytes
     --giga          show output in gigabytes
     --tera          show output in terabytes
     --peta          show output in petabytes
 -k, --kibi          show output in kibibytes
 -m, --mebi          show output in mebibytes
 -g, --gibi          show output in gibibytes
     --tebi          show output in tebibytes
     --pebi          show output in pebibytes
 -h, --human         show human-readable output
     --si            use powers of 1000 not 1024
 -l, --lohi          show detailed low and high memory statistics
 -t, --total         show total for RAM + swap
 -s N, --seconds N   repeat printing every N seconds
 -c N, --count N     repeat printing N times, then exit
 -w, --wide          wide output

     --help     display this help and exit
 -V, --version  output version information and exit
```

### <u>/proc/meminfo</u>
`cat` command와 보통 함께 쓰며, 사용 가능한 memory와 사용된 memory 양을 보고하는 가상 file입니다. <br>
시스템의 메모리 사용량과 kernel에서 사용하는 buffer 및 공유 memory에 대한 <b>실시간 정보</b>를 보여주며, 출력 방식은 architecture나 OS마다 조금 씩 다릅니다. <br>

```
$ cat /proc/meminfo

MemTotal:       32887408 kB
MemFree:         3944908 kB
MemAvailable:   18785152 kB
Buffers:          322772 kB
Cached:         20963772 kB
SwapCached:            0 kB
Active:         18147304 kB
Inactive:        9651724 kB
Active(anon):   13069268 kB
Inactive(anon):    28772 kB
Active(file):    5078036 kB
Inactive(file):  9622952 kB
Unevictable:       18472 kB
Mlocked:           18472 kB
SwapTotal:             0 kB
SwapFree:              0 kB
Dirty:                92 kB
Writeback:             0 kB
AnonPages:       6526752 kB
Mapped:          6698428 kB
Shmem:           6588732 kB
KReclaimable:     613932 kB
Slab:             807316 kB
SReclaimable:     613932 kB
SUnreclaim:       193384 kB
KernelStack:        7184 kB
PageTables:       158572 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:    16443704 kB
Committed_AS:   13397992 kB
VmallocTotal:   34359738367 kB
VmallocUsed:       40688 kB
VmallocChunk:          0 kB
Percpu:            10624 kB
HardwareCorrupted:     0 kB
AnonHugePages:   6096896 kB
ShmemHugePages:        0 kB
ShmemPmdMapped:        0 kB
FileHugePages:         0 kB
FilePmdMapped:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
Hugetlb:               0 kB
DirectMap4k:      772032 kB
DirectMap2M:    32782336 kB
DirectMap1G:     2097152 kB
```

## Reference
<https://phoenixnap.com/kb/linux-commands-check-memory-usage>