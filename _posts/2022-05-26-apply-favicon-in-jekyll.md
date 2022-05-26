---
published: true
title: "[Jekyll] Favicon 적용하기"
last_modified_at: 2022-05-26T15:24:00
categories:
  - jekyll
tags:
  - favicon
  - jekyll
---

## Favicon?
Favorite Icon의 약자로 웹페이지에 접속했을 때, 상단 탭에 보여지는 icon.<br>
즐겨찾기에 추가할 때에도 해당 Icon이 사용됩니다.<br>
<br>
아래는 제 blog의 최초 Favicon입니다. 아무런 셋팅도 하지 않았기 때문에 default icon이 보입니다.<br>
<img src="https://user-images.githubusercontent.com/90759236/170415058-ef2b0010-6ba5-4c05-9f04-2189b0852c7e.png" style="border: 1px solid grey; max-width: 80%; height: auto;"> <br>

### <u>나만의 Favicon 만들기</u>
아래 사이트에서 favicon을 직접 만들 수 있다고 합니다. ~~(저는 귀찮아서 안해봤습니다)~~ <br>
<http://www.degraeve.com/favicon/>

### <u>원하는 이미지 찾기</u>
저는 아래 blog에 있는 정보를 보고, 그 중 Flaticon(플랫아이콘)이라는 곳에서 무료 아이콘을 하나 받았습니다. <br>
<https://blog.wishket.com/%EC%A0%80%EC%9E%91%EA%B6%8C-%EA%B1%B1%EC%A0%95-%EC%97%86%EB%8A%94-%EB%AC%B4%EB%A3%8C-%EC%95%84%EC%9D%B4%EC%BD%98-%EC%82%AC%EC%9D%B4%ED%8A%B8/>

### <u>Favicon 만들기</u>
1. <https://realfavicongenerator.net/> 에 접속해서 방금 받은 icon 이미지를 선택해줍니다. <br>
<img src="https://user-images.githubusercontent.com/90759236/170417750-64855f7e-da5e-4fd8-827b-2f4b616e2eb7.png" style="border: 1px solid grey; max-width: 80%; height: auto;"> <br>

2. <b>"Select your Favicon image"</b>를 누르고 icon 이미지를 선택해주면 아래 화면이 나옵니다.<br>
<img src="https://user-images.githubusercontent.com/90759236/170421780-441daf2e-b10b-4c81-98aa-2ac8dd842ae7.png" style="border: 1px solid grey; max-width: 80%; height: auto;"> <br>
필요한 셋팅을 하시고 <u>맨 아래</u>에 있는 <b>"Generate your Favicons and HTML code"</b>를 선택하시면 됩니다.<br>
<img src="https://user-images.githubusercontent.com/90759236/170422004-f882437b-58ea-4cbf-b147-c1fd341b56cb.png" style="border: 1px solid grey; max-width: 80%; height: auto;"> <br>

3. 아래 page에서 <b>"Favicon package"</b>를 선택하면 생성된 Favicon이 download됩니다. <br>
제 경우(minimal-mistake)에는 생성된 HTML도 이용할 것이기 때문에 생성된 HTML code를 복사합니다. <br>
<img src="https://user-images.githubusercontent.com/90759236/170425199-1a8a6d76-0031-49e6-8c29-ad98b058df30.png" style="border: 1px solid grey; max-width: 80%; height: auto;"> <br>

### <u>Jekyll에 favicon 적용</u>
<i>_includes/_head/custom.html</i>에 위에서 복사한 HTML을 붙여넣기 해줍니다.
```html
<!-- start custom head snippets -->

<!-- insert favicons. use https://realfavicongenerator.net/ -->
<link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png">
<link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png">
<link rel="manifest" href="/site.webmanifest">
<link rel="mask-icon" href="/safari-pinned-tab.svg" color="#5bbad5">
<meta name="msapplication-TileColor" content="#da532c">
<meta name="theme-color" content="#ffffff">

<!-- end custom head snippets -->
```
위에서 바꿔야 할 내용이 있는데 바로 `href` tag입니다. 저는 보통 image들을 assets/images에 두는데, 해당 경로에 위에서 생성 후 다운 받은 favicon 파일들을 넣고 위 HTML의 `href`를 수정해줍니다.

```html
<!-- start custom head snippets -->

<!-- insert favicons. use https://realfavicongenerator.net/ -->
<link rel="apple-touch-icon" sizes="180x180" href="{{site.baseurl}}/assets/images/apple-touch-icon.png">
<link rel="icon" type="image/png" sizes="32x32" href="{{site.baseurl}}/assets/images/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="{{site.baseurl}}/assets/images/favicon-16x16.png">
<link rel="manifest" href="{{site.baseurl}}/assets/images/site.webmanifest">
<link rel="mask-icon" href="{{site.baseurl}}/assets/images/safari-pinned-tab.svg" color="#5bbad5">
<meta name="msapplication-TileColor" content="#da532c">
<meta name="theme-color" content="#ffffff">

<!-- end custom head snippets -->
```

### 적용 후 실제 변경 확인
<img src="https://user-images.githubusercontent.com/90759236/170428427-2c6e8208-e2de-4c4c-9f29-23ada491a66f.png" style="border: 1px solid grey; max-width: 80%; height: auto;"> <br>