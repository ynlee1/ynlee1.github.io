---
published: true
title: "[Git] Create git repository"
last_modified_at: 2022-05-09
categories:
  - git
tags:
  - git
  - github
---

## 새로운 repository 생성 방법
```sh
echo "# New repository" >> README.md      // 새로운 파일 생성 혹은 기존 작성된 파일 copy
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin {repository url}
git push -u origin main
```