---
published: true
title: "[Linux] CPU 정보 확인 방법"
last_modified_at: 2022-05-31T08:32:00
toc: true
toc_sticky: true
categories:
  - linux
tags:
  - linux
  - cpu
  - cpuinfo
---
## /proc/cpuinfo
/proc/cpuinfo는 시스템에 존재하는 CPU 수를 포함하여, 시스템에서 실행중인 processor 유형을 보여줍니다.
```sh
cat /proc/cpuinfo
```
<img src="https://user-images.githubusercontent.com/90759236/168754429-e9f66044-152d-4a8a-8a6a-e84c5c740fee.png" style="border: 1px solid grey; max-width: 80%; height: auto;">

### CPU 코어 전체 개수(+Hyper Threading)
```sh
cat /proc/cpuinfo | grep -c processor
```

### 실제(물리적인) CPU 개수 확인
```sh
grep "physical id" /proc/cpuinfo | sort -u | wc -l
```

### CPU당 물리 코어 개수 확인
```sh
grep "cpu cores" /proc/cpuinfo | tail -1
```

### Hyper Threading 여부
```sh
cat /proc/cpuinfo | egrep 'siblings|cpu cores' | head -2
```

### lscpu
/proc/cpuinfo에서 정보를 가져와 요약해서 CPU 정보를 보여주는 command입니다.
```sh
lscpu
```
<img src="https://user-images.githubusercontent.com/90759236/168758928-328013d4-8977-4cf6-90d9-ffbfc25f512b.png" style="border: 1px solid grey; max-width: 80%; height: auto;">

## Reference
https://nota.tistory.com/41