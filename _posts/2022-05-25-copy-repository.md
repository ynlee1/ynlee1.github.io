---
published: true
title: "[Git] 기존에 존재하는 repository 복제 방법 (Fork방식이 아닌)"
last_modified_at: 2022-05-25T13:13:00
categories:
  - git
tags:
  - git
  - github
  - mirror clone
---

## 기존에 존재하는 repository 복제 방법
만약 기존 Git repository 현재 버전을 복사하여 다른 project에서 활용하고자 하는 경우, <br>
혹은 사내 private Github 사용으로 인해 fork를 사용할 수 없는 경우, <br>
```git clone```의 ```mirror``` option 옵션을 이용해 기존의 Repository를 복제할 수 있습니다.

### Mirror clone
Mirror clone은 기존 repository의 모든 참조을 가져오는 것을 말합니다. <br>
여기서 참조란 commit log, branch를 포함한 모든 이력 및 repository 자체를 뜻합니다. <br>
아래와 같이 mirror clone을 통해 기존 repository를 clone합니다.
```sh
git clone --mirror {old_repository_url}
```

### Git(Hub)에 새로 만든 repository로 push
위 단계에서 mirror clone한 repository를 새로 만든 repository로 push합니다.
```sh
cd {old_repository_name}.git
git remote set-url --push orign {new_repository_url}
git push --mirror
```

GitHub에서 새로운 repository 생성 방법은 아래 post를 참조하시기 바랍니다.

[Blog link] <br>

{% assign posts = site.categories.github %}
{% for post in posts %}
  {% if post.title contains 'Token' %}
    {% include archive-single.html type=page.entries_layout %}
  {% endif %} 
{% endfor %}
