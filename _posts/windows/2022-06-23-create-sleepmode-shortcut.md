---
published: true
title: "[Windows] PC 잠금 쉽게 하기"
date: 2022-06-23
last_modified_at: 2022-06-23T11:33:00
toc: true
toc_sticky: true
categories:
  - windows
tags:
  - windows
  - lock
---

## Windows keyboard shortcut으로 PC 잠금 하기

Windows 단축키 <b><i>Windows + l</i></b>를 통해 PC를 잠금할 수 있습니다. 
* Windows: Windows keyboard shortcut
* l: 소문자 L
<br><br>

## Windows lock 바로가기 만들기
1. <b>바탕화면에서 마우스 우클릭 후 "새로만들기"->"바로가기" 선택 </b><br>
<img src="https://user-images.githubusercontent.com/90759236/175187628-bf67734c-4f81-45aa-80c6-cf1e90f1a1b7.png" style="border: 1px solid grey; max-width: 80%; height: auto;"> <br><br>

2. <b>항목 위치 입력에 <i>rundll32.exe</i> 추가</b><br>
항목 위치 입력에 아래의 내용을 입력 후 "다음"을 선택합니다.

    ```
    rundll32.exe user32.dll,LockWorkStation
    ```

    <img src="https://user-images.githubusercontent.com/90759236/175187968-d4182126-4342-46d3-a630-2348ef55baf6.png" style="border: 1px solid grey; max-width: 80%; height: auto;">
<br>

1. <b>바로가기 이름을 지정 후 "마침" 선택</b><br>
바로 가기에 사용할 이름을 입력해줍니다. 저의 경우는 sleep.exe이라는 이름을 입력했습니다. <br>
<img src="https://user-images.githubusercontent.com/90759236/175188220-70a77572-b862-484e-8ce8-b130913c96f0.png" style="border: 1px solid grey; max-width: 80%; height: auto;"> <br><br>

4. <b>완료 후 test 및 작업 표시줄에 고정</b><br>
저의 경우 해당 바로가기를 작업 표시줄에 고정에서 사용합니다. 각자 편하신 방법으로 실행하시면 될 것 같습니다. <br>
<img src="https://user-images.githubusercontent.com/90759236/175188438-5a581168-782a-4ea4-9946-375bbb8c7c42.png" style="border: 1px solid grey; max-width: 80%; height: auto;"> <br><br>

5. <b>(Optional) 아이콘 변경</b><br>
만약 아이콘 변경을 원한다면, 바로가기 우클릭 후 "속성"->"아이콘 변경"을 선택하여 아래 경로를 입력해주면 Windows에서 기본적으로 사용하는 icon들을 선택할 수 있습니다. <br>
    
    ```
    %SystemRoot%\System32\SHELL32.dll
    ```

<br>

## Reference
[Clien 팁과강좌](https://www.clien.net/service/board/lecture/17331014?od=T31&po=1&category=0&groupCd=)
