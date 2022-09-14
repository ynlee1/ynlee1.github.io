---
published: true
title: "[GitHub] 조직 내 Two-factor authentication 활성화"
date: 2022-09-14
last_modified_at: 2022-09-14T15:36:00
toc: true
toc_sticky: true
categories:
  - github
tags:
  - github
  - two-factor authentication
  - github organization setting
---

## Two-factor authentication
Two-factor authentication은 계정을 더욱 안전하게 보호하는 추가 보안 절차로, 사용자의 ID/Password 인증만이 아닌 추가로 요청받은 정보로 입력해야 계정 접근 권한을 얻게되는 것을 말합니다. <br><br>
GitHub에서도 자체적으로 Two-factor authentication 기능을 제공하며, 인증 방식은 SMS나 Authenticator같은 mobile application이 있습니다. <br>


## GitHub 조직에서 Two-factor authentication 활성화
1. 조직 main page에서 <b>"Settings"</b> 선택 <br>
<img src="https://user-images.githubusercontent.com/90759236/190079419-62d19a29-211b-4889-816e-289ed55eb5fb.png" style="border: 1px solid grey; max-width: 90%; height: auto;"><br>

2. 좌측 menu에서 <b>"Authentication security"</b> 선택 <br>
<img src="https://user-images.githubusercontent.com/90759236/190079782-4f58dc60-59e8-41c2-81c9-edfbd3a8bda8.png" style="border: 1px solid grey; max-width: 35%; height: auto;"><br>

3. Two-factor authentication 메뉴에서 아래 checkbox 선택 후 <b>"Save"</b> 선택 <br>
<img src="https://user-images.githubusercontent.com/90759236/190080514-37399347-6dac-4b19-b8d8-051e2c561188.png" style="border: 1px solid grey; max-width: 85%; height: auto;"><br>
    - Ref.1) 만약 위 checkbox 및 "Save" 버튼이 활성화되지 않는다면 본인 계정(조직 admin 계정)에 TFA가 활성화되어 있지 않아서 입니다. 녹색 box(<b>"your account"</b>)를 클릭해서 본인 계정의 TFA를 활성화 한 후에 다시 시도하시기 바랍니다.
    - Ref.2) 이미 초대된 각 사용자 계정의 TFA를 활성화 하지 않은 상태에서 조직의 TFA를 활성화할 시 해당 계정이 조직에서 제거 됩니다. 

4. 활성화 완료 후 화면 확인<br>
<img src="https://user-images.githubusercontent.com/90759236/190082467-384508b2-43d7-408e-842f-3a72e5476e33.png" style="border: 1px solid grey; max-width: 85%; height: auto;"><br>
