---
published: true
title: "[Jekyll] Minimal Mistake에서 font 및 font size 변경 방법"
last_modified_at: 2022-05-29T23:43:00
categories:
  - jekyll
tags:
  - jekyll
  - font
  - font size
  - minimal mistake
---

## Minimal Mistake에서 기본 font 변경 방법
Font를 변경해볼까 하고 font 변경 방법에 대해 찾아봤습니다. 대부분 구글 폰트에 있는 무료 폰트를 사용하는 것 같습니다. <br>
<https://fonts.google.com/> <br>

일단 언어는 한국어로 셋팅하고, 나오는 폰트 중 하나를 골라줍니다. 저는 나눔고딕으로 설정했습니다.
<img src="https://user-images.githubusercontent.com/90759236/170866203-1cc5ad0e-52aa-42c3-aa46-9df0ca3e7369.png" style="border: 1px solid grey; max-width: 70%; height: auto;"><br>

폰트를 고르면 아래처럼 두깨를 고를 수 있고, 실제 테스트도 가능합니다. 저는 Regular 400, Bold 700, ExtraBold 800을 선택했습니다. 오른쪽에 있는 "<u>Select this style</u>"를 선택해줍니다.<br>
<img src="https://user-images.githubusercontent.com/90759236/170866395-fa9c1a19-1f5e-4a30-bd6d-37933ffd2780.png" style="border: 1px solid grey; max-width: 70%; height: auto;"><br>
<img src="https://user-images.githubusercontent.com/90759236/170866405-36d78196-743f-490a-9127-87cdb2fc6cd6.png" style="border: 1px solid grey; max-width: 70%; height: auto;"><br>

우측에 팝업창이 나오면, Use on the web에서 "<u>@import</u>"를 선택해줍니다. <br>
<img src="https://user-images.githubusercontent.com/90759236/170870374-720f10ed-67df-47f9-80f7-e4d7165dbf49.png" style="border: 1px solid grey; max-width: 60%; height: auto;"><br>

이제 위에 있는 `@import url`과 `CSS rule`을 이용해 코드를 변경해봅시다!<br>
구글링을 해보면 방법이 좀 다양한데, 저는 아래와 같은 방법을 사용했습니다. 
<br><br><i>assets/css/main.scss</i> 파일을 열어서 아래 부분을 추가해줍니다.<br>
`@import url("https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@100;300;400;500;700;900&display=swap"); // font`
* 주의: <b>맨 윗줄의 '---'는 삭제하거나 변경하시면 안됩니다!</b>

```scss
--- 
# Only the main Sass file needs front matter (the dashes are enough) 
--- 

@charset "utf-8";

@import "minimal-mistakes/skins/{{ site.minimal_mistakes_skin | default: 'default' }}"; // skin
@import "minimal-mistakes"; // main partials
@import url('https://fonts.googleapis.com/css2?family=Nanum+Gothic:wght@400;700;800&display=swap'); // font
```

다음은 <i>_sass/minimal-mistakes/_variables.scss</i>에서 아래 내용을 수정해줍니다.
```scss
/* system typefaces */
$serif: Georgia, Times, serif !default;
$sans-serif: 'Nanum Gothic', -apple-system, BlinkMacSystemFont, 'Roboto', 'Segoe UI', 'Helvetica Neue',
  'Lucida Grande', Arial, sans-serif !default;
$monospace: 'Nanum Gothic', Monaco, Consolas, 'Lucida Console', monospace !default;
```
* <i>sans-serif</i>에 `'Nanum Gothic',` 추가
* <i>monospace</i>에 `'Nanum Gothic',` 추가

## Font size 변경
<i>_sass/minimal-mistakes/_reset.scss</i>에서 아래 font-size를 원하는 size로 변경하면 됩니다.
```scss
html {
  /* apply a natural box layout model to all elements */
  box-sizing: border-box;
  background-color: $background-color;
  font-size: 14px;

  @include breakpoint($medium) {
    font-size: 14px;  // default 18px
  }

  @include breakpoint($large) {
    font-size: 16px;  // default 20px
  }

  @include breakpoint($x-large) {
    font-size: 18px;  // default 22px
  }

  -webkit-text-size-adjust: 100%;
  -ms-text-size-adjust: 100%;
}
```