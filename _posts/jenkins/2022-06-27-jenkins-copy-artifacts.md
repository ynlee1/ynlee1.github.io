---
published: true
title: "[Jenkins] Jenkins copyArtifacts"
date: 2022-06-27
last_modified_at: 2022-06-27T13:01:00
toc: true
toc_sticky: true
categories:
  - jenkins
tags:
  - jenkins
  - copyArtifacts
  - pipeline
---

## About <i>copyArtifacts</i>
Jenkins에서 pipeline을 구성하다 보면 특정 job의 결과물들을 현재 경로로 copy해와야 하는 경우가 자주 생깁니다. <br><br>
Linux상에서 해당 작업을 할 경우에 절대 경로, 혹은 현재 workspace 기준 상대 경로로 접근하기가 쉬운데, 이 경우 job의 PATH가 바뀔 시 code 수정을 다시 해줘야 하는 불편함이 있습니다. <br><br>
이를 편하게 하기 위해 Jenkins에서는 <i><b>copyArtifacts</b></i>라는 plugin을 제공합니다. <br><br>

## How to use <i>copyArtifacts</i>

### Install <i>copyArtifacts</i> plugin
1. Jenkins web의 왼쪽 상단 menu에서 <b>"Jenkins 관리"</b> 선택<br>
<img src="https://user-images.githubusercontent.com/90759236/175844492-e53652c2-85f2-4ddf-b260-2463a83d8dcd.png" style="border: 1px solid grey; max-width: 30%; height: auto;">

2. System Configuration menu에서 <b>"플러그인 관리"</b> 선택<br>
<img src="https://user-images.githubusercontent.com/90759236/175844667-7b26c6fd-ea84-4084-86bf-10fa2aa4d5d2.png" style="border: 1px solid grey; max-width: 80%; height: auto;">

3. <b>"설치 가능"</b> tab 선택 후 <b>"Copy Artifact"</b> 검색 및 설치<br>
<img src="https://user-images.githubusercontent.com/90759236/175844855-de764ed3-3801-46d9-a886-6a9007fcd53b.png" style="border: 1px solid grey; max-width: 60%; height: auto;">

    참고로 저는 이미 설치를 했기 때문에 "설치된 플러그인 목록"에서 확인할 수 있습니다.<br>
    <img src="https://user-images.githubusercontent.com/90759236/175845043-9eec5c91-0aff-4451-9081-84cdd8be4acf.png" style="border: 1px solid grey; max-width: 60%; height: auto;">
<br>

### <i><b>copyArtifacts</b></i> parameters
아래는 <i>copyArtifacts</i>의 각 parameter에 대한 설명입니다.

| parameter | type | description |
| :---------: | :-----: | :----------------------------------------------------------- |
| projectName | string | Artifact를 복사할 Jenkins job name |
| excludes(optional) | string | 복사할 artifacts에서 제외할 artifact 경로 및 패턴 |
| filter(optional) | string | 모든 artifacts를 복사할 때는 공백 혹은 사용하지 않으면 되며, 특정 artifacts를 복사할 때에 사용. 특정 artifacts의 (상대)경로 및 패턴 |
| fingerprintArtifacts(optional) | boolean | Artifact의 MD5 checksum을 기록, 빌드를 추적하는데 사용 |
| flatten(optional) | boolean | 복사할 artifact의 directory 구조는 copy해오지 않음 |
| optional(optional) | boolean | copyArtifacts애서 실패가 발생하더라도 step 실패가 발생하지 않음 |
| parameters(optional) | string | 특정 매개변수 또는 다른 빌드 변수와 일치하는 build만 선택하도록 필터링할 때 사용. 예를 들어 Foo=bar, BAZ=true는 매개변수 Foo가 bar로 설정되고, BAZ 확인란이 선택된 상태에서 실행된 빌드만 검사 |
| selector(optional) | BuildSelector | latest successful, stable build, latest 등 artifact를 복사할 build state를 선택 |
| target(optional) | string | 복사할 대상 directory 지정 시 사용 |

아래는 위 parameter중 selector에서 사용할 수 있는 list입니다.<br>

| name | description |
| :---------: | :----------------------------------------------------------- |
| lastSuccessful | lastest successful build |
| specific | specific build |
| permalink | specified by permalink |
| lastCompleted | lastest completed build(ignoring build status) |
| lastSavedBuild | lastest saved build(marked "keep forever") |
| buildParameter | specified by a build parameter |
| upstream | upstream build that triggered this job |

<br>

### 사용 예제
<script src="https://gist.github.com/ynlee1/145b90abd12bf1007eeb10e6d96efd28.js"></script>

* 'job-A' job을 parameter 'A'와 함께 trigger 후, job-A의 결과물들 중 확장자가 'txt'로 끝나는 file들을 현재 workspace 기준 <i>'Archive'</i> directory로 copy

<br>

## Reference
- [Jenkins Guide](https://www.jenkins.io/doc/pipeline/steps/copyartifact/)