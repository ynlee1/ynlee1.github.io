---
published: true
title: "[Jekyll] GitHub Blog with minimal-mistake"
last_modified_at: 2022-05-30T08:31:00
toc: true
toc_sticky: true
categories:
  - jekyll
tags:
  - github
  - jekyll
  - minimal-mistake
---

## Minimal-mistake
장점: 커스터마이징의 장점을 가지고 있으며, 자유도가 높음

### What is Jekyll(지킬)?
Static Website Builder. Markup language로 글을 작성하면 미리 정의해 놓은 규칙에 따라 정적 웹사이트를 만들어 준다.

### Markup language?
Tag등을 이용하여 문서나 data 구조를 작성하는 언어
* HTML이나 XML등이 Markup 언어에 해당

### Markdown language?
Markup 언어 종류의 하나로 Markup 문법을 좀 더 쉽게 변경한 언어. 읽기와 쓰기가 쉽다는 장점을 가지고 있음.
* .md

### How to install
1. Ruby download
    - Jekyll이 32bit이기 때문에 x86으로 설치
    - with devkit으로 설치
    - [Download Link](https://rubyinstaller.org/downloads/)<br>
    <img src="https://user-images.githubusercontent.com/90759236/167263822-5d2c6961-9d24-494f-a513-e07ac76c5faf.png" style="border: 1px solid grey">

2. Install Jekyll
    - Windows Powershell이나 cmd에서 아래 command 실행
      ```sh
      gem install jekyll
      ```

3. Ruby 및 Jekyll 정상 설치 여부 확인
    ```sh
    ruby -v
    ```
    ```sh
    jekyll -v
    ```

4. Clone minimal-mistakes
    ```sh
    git clone https://github.com/mmistakes/minimal-mistakes
    ```

5. 아래의 불필요한 파일들 삭제
    - Directory: .github, test
    - File: editorconfig, .gitattributes, .travis.yml, CHANGELOG.md, README.md, screenshot.png, screenshot-layouts.png
    - Etc: docs/pages/about.md --> ```bundle exec jekyll serve``` command에서 error 발생

6. docs/_pages directory를 상위 directory로 이동

7. [github account].github.io 이름의 repository 생성 및 위에서 clone한 내용을 해당 repo로 commit & push

8. Install bundle
github로 push해서 link로 확인하는 방법도 있지만, 이는 딜레이도 있어 불편, 로컬서버에서 확인 후 적용하는 것이 좋음
    ```sh
    gem install bundler
    ```
    ```sh
    bundle update
    ```
    ```sh
    bundle exec jekyll serve
    ```

9. http://127.0.0.1:4000 접속해서 정상 동작하는지 확인
<img src="https://user-images.githubusercontent.com/90759236/167263882-8c4abc3f-583a-491e-b4ec-34e57a7ed19c.png" style="border: 1px solid grey">

1.  _config.yml에서 기본 설정 후 commit & push. [github account].github.io에 정상 반영 여부 확인