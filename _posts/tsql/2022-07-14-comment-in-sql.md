---
published: true
title: "[ms-sql] 주석 처리"
date: 2022-07-14
last_modified_at: 2022-07-14T13:35:00
toc: true
toc_sticky: true
categories:
  - tsql
tags:
  - sql
  - comment
---

* 작성일: 2022/07/14

## SQL에서 주석 처리
다른 일반적인 언어와 마찬가지로 single line 주석과 multi line 주석이 있습니다.<br><br>

### Single line comment
<b>'--'</b>를 사용한 단일 라인 주석 처리 <br>

```sql
-- single line comment
select * from contents
```

### Multi line comment
<b>'/*, */'</b>를 사용한 여러 라인 주석 처리 <br>

```sql
/* 
multi line comment
select all 
*/
select * from contents
```