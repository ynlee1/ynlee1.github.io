---
published: true
title: "[Jekyll] minimal-mistakes skin 변경 방법"
date: 2022-06-27
last_modified_at: 2022-06-27T14:16:00
toc: true
toc_sticky: true
categories:
  - jekyll
tags:
  - jekyll
  - minimal-mistakes
  - skin
---

## Minimal-Mistakes theme에서 skin 변경하는 방법
Jekyll에서 minimal-mistakes theme에서 skin 변경 하는 방법은 두 개의 파일만 수정해주면 됩니다. <br>
하나는 <i>_config.yml</i>이고 다른 하나는 <i>main.scss</i>입니다. <br>
<br>

### <i>_config.yml</i> 수정
_config.yml의 <i>minimal_mistakes_skin</i> 값을 원하는 skin으로 수정해줍니다. <br>
skin에 대한 자세한 정보는 <https://mmistakes.github.io/minimal-mistakes/docs/configuration/>에서 확인하실 수 있습니다. <br> 

<br> 저는 "air" skin으로 변경했습니다. <br><br>

```yml
# Theme Settings
#
# Review documentation to determine if you should use `theme` or `remote_theme`
# https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/#installing-the-theme

# theme                  : "minimal-mistakes-jekyll"
# remote_theme           : "mmistakes/minimal-mistakes"
minimal_mistakes_skin    : "air" # "air", "aqua", "contrast", "dark", "dirt", "neon", "mint", "plum", "sunrise"
```
<br>

### <i>main.scss</i> 수정
<i>assets/css/main.scss</i>에서 skin 관련 import 부분을 수정해줘야 합니다. <br>
기존에 있었던 import line을 지우고(혹시 모를 rollback을 위해 주석 처리), <i>_config.yml</i> file에서 셋팅한 <i>minimal_mistakes_skin</i>을 넣어줍니다. <br>

```scss
---
# Only the main Sass file needs front matter (the dashes are enough) 
--- 

@charset "utf-8";

{% raw %}/{% endraw %}/ @import "minimal-mistakes/skins/{% raw %}{{{% endraw %} site.minimal_mistakes_skin | default: 'default' {% raw %}}}{% endraw %}"; // skin
@import "minimal-mistakes/skins/{% raw %}{{% endraw %}{ site.minimal_mistakes_skin {% raw %}}{% endraw %}}"; // skin
```
<br><br>

## Reference
* Minimal Mistakes guide: <https://mmistakes.github.io/minimal-mistakes/docs/configuration>
