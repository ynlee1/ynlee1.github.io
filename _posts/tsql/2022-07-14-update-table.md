---
published: true
title: "[ms-sql] UPDATE를 이용한 data 변경"
date: 2022-07-14
last_modified_at: 2022-07-14T13:50:00
toc: true
toc_sticky: true
categories:
  - tsql
tags:
  - tsql
  - mssql
  - update
---

* 작성일: 2022/07/14

## UPDATE
SQL data를 변경하기 위해 사용합니다. <br><br>

### UPDATE all value of column
Table 내 특정 column 모든 value를 변경

```sql
UPDATE dbo_user SET phone = '0'
```

* 모든 user의 phone#를 '0'으로 변경

<br>

### UPDATE specific value of column
특정 column 특정 값을 변경

```sql
UPDATE dbo_user SET phone = '012-3456-xxxx' where u_name = '홍길동'
```

* 이름이 '홍길동'인 유저의 phone#를 '012-3456-xxxx'로 변경

