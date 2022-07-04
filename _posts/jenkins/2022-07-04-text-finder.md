---
published: true
title: "[Jenkins] Text Finder plugin"
date: 2022-07-04
last_modified_at: 2022-07-04T10:42:00
toc: true
toc_sticky: true
categories:
  - jenkins
tags:
  - jenkins
  - text finder
  - plugin
---

## Text Finder Plugin
<b>Text Finder</b> plugin은 Jenkins job에서 특정 file이나 console log에 지정한 문자열이 존재하는지 확인 후 job status를 변경할 수 있도록 해줍니다. <br>

주로 Jenkins Job 내에서 <b>build failure</b>를 check하지 못하는 build 실패 상황이 발생할 경우, 혹은 warning이기는 하나 중요한 warning이라 build 상태를 failure로 변경하고 싶은 경우에 해당 plugin을 사용합니다. <br>

해당 post에서는 freestyle job에서 Text Finder를 설정하는 방법에 대해 다룹니다. <br>
Pipeline job에서 해당 plugin을 사용하고 싶은 경우에는 아래 URL을 참조하시기 바랍니다. <br>
* <https://plugins.jenkins.io/text-finder/>

<br>

### Install 'Text Finder' plugin
1. 우측 상단의 <b>'Jenkins 관리'</b> menu 선택 후 <b>"플러그인 관리"</b> 선택<br>
<img src="https://user-images.githubusercontent.com/90759236/177069283-459399c2-74e2-4500-a82c-c12fc1e83f18.png" style="border: 1px solid grey; max-width: 40%; height: auto;"><br>
<img src="https://user-images.githubusercontent.com/90759236/177069429-9d194a16-15a8-4074-89e1-83b7392a1d38.png" style="border: 1px solid grey; max-width: 80%; height: auto;"><br>

2. <b>'설치 가능'</b> tab에서 <b>Text Finder</b> 검색 후 설치<br>
<img src="https://user-images.githubusercontent.com/90759236/177069581-21026e28-c191-4e18-8c06-6d0c5bb4ef75.png" style="border: 1px solid grey; max-width: 80%; height: auto;"><br>

<br>

### Jenkins job configure에서 Text Finder 설정
1. Job에서 <b>'구성(Configure)'</b> 메뉴 선택<br>
<img src="https://user-images.githubusercontent.com/90759236/177069866-84821a49-0ed6-4926-9827-26b9921fbfa1.png" style="border: 1px solid grey; max-width: 40%; height: auto;"><br>

2. <b>'빌드 후 조치 추가'</b> 메뉴에서 <b>'Search files or the consol log...'</b> 선택<br>
<img src="https://user-images.githubusercontent.com/90759236/177069978-12c4c2a3-acb0-4b8b-a248-c71f950a5967.png" style="border: 1px solid grey; max-width: 40%; height: auto;"><br>

3. 원하는 방식에 맞게 Text Finder 설정<br>
<img src="https://user-images.githubusercontent.com/90759236/177070046-d7fa7fe5-2d13-4cfc-a063-eee136ddc0ca.png" style="border: 1px solid grey; max-width: 80%; height: auto;"><br>
   * <b><u>Regular expression</u></b>: 찾고자 하는 string이나 정규식
   * <b><u>Files</u></b>: Text를 찾고자 하는 파일, 비어있다면 File 내 검색을 하지 않음
   * <b><u>Also search the console output</u></b>: console output에서도 text를 검색
   * <b><u>Build result</u></b>: 아래 'Change condition'에 맞는 조건 충족 시 setting할 Build 결과
   * <b><u>Change condition</u></b>: Text 검색 결과에 따른 build result 변경을 어떤 조건으로 할지 setting





