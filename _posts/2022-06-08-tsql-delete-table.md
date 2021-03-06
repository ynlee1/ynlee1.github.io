---
published: true
title: "[ms-sql] delete - delete data from DB"
date: 2022-06-08
last_modified_at: 2022-07-14T13:36:00
toc: true
toc_sticky: true
categories:
  - tsql
tags:
  - tsql
  - delete
---

## delete
DB에서 data를 삭제하는 delete 문입니다. <br>
delete 다음에 삭제할 대상 table 명, table에서 어떤 data를 지울 것인지 정하는 where절을 붙여주면 됩니다. <br>
만약 where절이 없다면 table에 있는 전체 data가 삭제 됩니다. <br>

### Example 1. delete all data in table
```sql
delete from ['table name']
```

### Example 2. delete specific data in table
```sql
delete from ['table name'] where 'key' = 'value';
```

(2022/07/14 Update)<br>
<u><i>위 예제에서 <b>key</b>는 <b>" ' "</b>(single quotation marks) 없이 사용해야 합니다.</i>