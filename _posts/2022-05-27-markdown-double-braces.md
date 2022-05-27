---
published: true
title: "[Jekyll] Markdown에서 이중 중괄호가 안보이는 이슈 해결"
last_modified_at: 2022-05-27T09:08:00
categories:
  - markdown
tags:
  - markdown
  - double braces
---

## Markdown에서 중괄호가 실제 web에서 보이지 않는 이슈 해결
Markdown 작성 중 HTML code를 삽입 시 이중 중괄호(double curly braces)가 web상에 보이지 않는 이슈가 있습니다. 아마도 liquid 문법때문인 것 같습니다. <br>

Liquid는 Ruby 기반의 open source template 언어로 동적 컨텐츠를 load하는데 사용하는 언어라고 합니다. Jekyll은 liquid언어를 사용하며, 이점 때문에 이중 중괄호가 문자로 처리되지 않는 것 같습니다. <br>

아래는 Liquid blog입니다. Introduction을 보시면 오브젝트나 변수 사용 시 double curly braces를 사용한다고 나옵니다.<br>
<https://shopify.github.io/liquid/basics/introduction/> <br>

그래서 실제 HTML code를 Markdown에 작성할 때 이중 중괄호가 liquid문법에서 처리되지 않도록 예외처리를 해줘야 하는데 이를 위해 사용하는 liquid 태그가 있습니다.<br>
==> <b>\{\% raw \%\}</b>와 <b>\{\% endraw \%\}</b>
<br>
`raw` tag는 임시로 tag 처리를 비활성화 해주는 역할을 하며 아래처럼 사용하시면 됩니다.
```html
\{\% raw \%\}
<link rel="apple-touch-icon" sizes="180x180" href="\{\{site.baseurl\}\}/assets/images/apple-touch-icon.png">
\{\% endraw \%\}
```






