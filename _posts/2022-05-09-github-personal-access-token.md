---
published: true
title: "[GitHub] GitHub Personal Access Token"
last_modified_at: 2022-05-09T12:54
categories:
  - github
tags:
  - github
  - pat
  - action
---

## GitHub Personal Access Token?
Git이나 GitHub에서 clone이나 push를 할 때, 과거에는 ID/Password 혹은 SSH 인증 방식을 사용했었습니다. 현재는 ID/Password를 통한 인증방식을 사용할 수 없는 것으로 알고 있습니다. 대신에 Personal Access Token이란 값을 통해서 사용자 인증을 진행하는데, 이 글에서는 Personal Access Token 생성 방법을 다룹니다.

### 1. 계정 메뉴에서 "Settings" 선택
GitHub login 후 우측 상단에 본인이 선택한 Profile picture가 보일 겁니다. 해당 그림을 눌러 "Settings"에 진입합니다.
<img src="https://user-images.githubusercontent.com/90759236/167339858-e1e306b1-7010-4df9-ae4c-ca671264d769.png" style="border: 1px solid grey">

### 2. 좌측 메뉴 하단의 "Developer Settings" 선택
<img src="https://user-images.githubusercontent.com/90759236/167339991-ab01bb2c-ad7e-4070-a163-92800c1f95c3.png" style="border: 1px solid grey">

### 3. 좌측 메뉴에서 "Personal access tokens" 선택
저는 이미 auth라는 이름으로 생성한 token이 있기 때문에 아래처럼 보입니다. "Generate new token"을 선택
<img src="https://user-images.githubusercontent.com/90759236/167340195-d1587452-e9fc-4856-9ecf-cfc97a033f7d.png" style="border: 1px solid grey">

### 4. GitHub Password 입력 후 "Confirm password" 선택
사용자 확인을 위해 비밀번호를 입력합니다.<br>
<img src="https://user-images.githubusercontent.com/90759236/167340273-6687e880-a68e-4288-bcd9-ebcb0c0530a0.png" style="border: 1px solid grey">

### 5. Access Token 생성
* Note: token의 용도를 적어줍니다.
* Expiration: 해당 Token의 사용 기간을 설정합니다. 해당 기간 이후에는 생성한 token이 만료됩니다.
* Select scopes: Token에 부여할 권한을 설정합니다. 원하는 권한을 부여하면 됩니다. repo 관련 설정뿐만 아니라 다른 설정도 많으니 잘 보시고 설정하시기 바랍니다. 아래 그림에는 repo 관련 권한까지만 나와있습니다.
<img src="https://user-images.githubusercontent.com/90759236/167340623-52e0eeb6-d551-4970-9be0-c02f3311e2eb.png" style="border: 1px solid grey">

모든 설정 완료 후 "Generate token" 선택

### 6. 생성된 token value를 복사
<b><u>해당 값은 추후에 다시 확인할 수 없습니다.</u></b> 꼭 안전한 곳(?)에 복사해두셔야 합니다.
<img src="https://user-images.githubusercontent.com/90759236/167340908-4331af4f-5fe5-48a9-8f94-2b50019e0fe1.png" style="border: 1px solid grey">

### 7. 사용 방법
GitHub에 push나 local로의 clone시 password를 요구할 때 해당 token을 입력하면 됩니다. GitHub Action시에도 해당 token을 이용할 수 있습니다(권한 설정이 알맞게 되어 있어야 동작합니다).