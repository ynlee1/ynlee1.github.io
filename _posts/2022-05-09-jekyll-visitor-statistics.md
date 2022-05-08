---
published: true
title: "[Jekyll] Visitor statistics with Google Analytics"
last_modified_at: 2022-05-09
categories:
  - jekyll
tags:
  - github
  - jekyll
  - google-analytics
---

## Google Analytics
Google에서 <b>무료</b>로 제공하는 Web 분석 서비스라고 합니다. Google Analytics를 이용해 GitHub blog의 방문자 통계를 확인할 수 있습니다.

## Google Analytics 등록

### 1. Google Analytics home에 접속
https://analytics.google.com/
<img src="https://user-images.githubusercontent.com/90759236/167304249-a5d0fe4f-98b3-4dc7-b0d9-587daeaf42f1.png" style="border: 1px solid grey">
<br>"측정 시작" 선택

### 2. 계정 설정
계정 이름의 경우 통계에 직접적인 영향이 없다고 합니다. 편하게 작성해도 될 것 같습니다.<br>
아래 4가지 선택 사항에 대해서는 저는 모두 선택했습니다.
* [x] Google 제품 및 서비스
* [x] 벤치마킹
* [x] 기술 지원
* [x] 계정 전문가
<img src="https://user-images.githubusercontent.com/90759236/167304330-15bc0fb7-fd8e-42fc-8f46-a51756a1331e.png" style="border: 1px solid grey"><br>
모두 작성 및 선택 후 "다음"을 선택합니다.

### 3. 속성 설정
* 속성 이름: GitHub blog 이름을 입력합니다([github account].github.io)
* 보고 시간대: "대한민국/대한민국 시간" 선택
* 통화: "대한민국 원 (KRW)" 선택
<img src="https://user-images.githubusercontent.com/90759236/167304569-fb24faf1-1645-42fc-9f94-6a3fc9a75a76.png" style="border: 1px solid grey"><br>
또한 고급 옵션에서 아래 내용 추가가 필요합니다.
* Jekyll minimal-mistakes는 Google Analystics 4를 지원하지 않는 것으로 보입니다. 
  * 2023년 7월 1일부터 UA 속성 데이터를 수집하지 않는다고 합니다. 다른 방법을 찾아보는 것이 필요할 것 같습니다.
<img src="https://user-images.githubusercontent.com/90759236/167307429-a257e4c6-1401-4dc7-8b84-2c716d2dc255.png" style="border: 1px solid grey"><br>

### 4. 비지니스 정보
중요한 건 아닌 것 같아 대충(?) 선택해줬습니다.
<img src="https://user-images.githubusercontent.com/90759236/167304753-1defedd7-5d74-49af-bb29-28513b87b387.png" style="border: 1px solid grey"><br>
* "만들기"를 선택하면 아래 서비스 약관 동의가 나옵니다.
<img src="https://user-images.githubusercontent.com/90759236/167304864-eee84d77-9aa6-43e1-b4f5-c5474d211a8c.png" style="border: 1px solid grey">

### 5. 이메일 커뮤니케이션
만들기가 완료된 후 아래와 같은 이메일 커뮤니케이션 팝업창이 나옵니다. 필요한 내용을 선택 후 "저장"버튼을 click해주세요.
<img src="https://user-images.githubusercontent.com/90759236/167304918-aec32641-dbc2-4fc8-86f3-d8ea86a4ee1a.png" style="border: 1px solid grey">

### 6. 데이터 스트림 설정 1
데이터 스트림을 만들어야 합니다. 데이터 스트림을 만들어야 Jekyll에 필요한 정보 "측정 ID"를 얻을 수 있습니다. "웹(Web)"을 선택합니다.
<img src="https://user-images.githubusercontent.com/90759236/167305023-28077a5e-3a04-45e2-a99e-8d6c1654176a.png" style="border: 1px solid grey">

### 7. 데이터 스트림 설정 2
웹 사이트 URL과 스트림 이름을 입력해 줍니다. 제 경우에는 스트림 이름을 웹 사이트 URL과 동일하게 작성했습니다. 작성 및 "향상된 측정" 설정 후 "스트림 만들기"를 클릭해줍니다.
<img src="https://user-images.githubusercontent.com/90759236/167305128-9448cb45-c431-441a-a87a-292ff6c716c2.png" style="border: 1px solid grey">

### 8. 측정 ID 복사
모든 과정이 완료되면 "측정 ID"를 바로 얻을 수 있습니다.
<img src="https://user-images.githubusercontent.com/90759236/167305335-dc75f8de-2c91-4506-981c-5b02e32f7bc2.png" style="border: 1px solid grey">

## _config.yml에 측정 ID 작성
아래 코드 처럼 _config.yml를 변경 후 commit/push해주세요.<br>
```sh
# Analytics
analytics:
  provider               : "google-gtag" # false (default), "google", "google-universal", "google-gtag", "custom"
  google:
    tracking_id          : "UA-XXXXXXXXX-X"
    anonymize_ip         : # true, false (default)
```
UA tracking_id는 애널리틱스 옆 계정 정보를 클릭하면 보실 수 있습니다.
<img src="https://user-images.githubusercontent.com/90759236/167307516-f58b0266-5986-46b7-9fcb-bb72ca07746a.png" style="border: 1px solid grey">

## 확인 방법
모든 setting이 끝나고 적당한 시간이 지나면 Google Analytics의 UA에서 웹사이트 데이터를 확인할 수 있습니다.
<img src="https://user-images.githubusercontent.com/90759236/167307639-0b770872-17df-4fb2-bb2e-e5332f30227d.png" style="border: 1px solid grey">