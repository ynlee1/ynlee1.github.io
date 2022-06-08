---
published: true
title: "[Python] About Poetry"
date: 2022-06-03
last_modified_at: 2022-06-08T10:17:00
toc: true
toc_sticky: true
categories:
  - python
tags:
  - python
  - poetry
---

## Poetry
Poetry는 python의 의존성 관리 및 packaging을 위한 tool로 <i>pyproject.toml</i> file을 이용해 패키지를 관리합니다. <br>
흔히 javascript나 typescript에서 사용하는 npm, yarn과 동일한 역할을 한다고 보셔도 됩니다. <br>
아래는 poetry project github 입니다.<br>
- <https://github.com/python-poetry/poetry>

## pip vs. poetry
Python은 이미 'pip'라는 package 관리자가 있습니다. 하지만 pip는 자체적으로 프로젝트 내 package 관리를 하기 어렵고, 개발자가 직접 requirements.txt를 작성해줘야 합니다. <br>
<b>즉 npm, yarn에서 보던 lock file이 존재하지 않습니다.</b><br><br>
또한, pip는 항상 전역에 모든 package를 설치합니다. 이는 프로젝트별 package 버전 관리를 할 수 없다는 뜻입니다. <br>물론 virtualenv라는 tool을 이용해 환경을 분리할 수는 있지만 각자 관리를 해줘야 하는 불편함을 가지고 있습니다.<br><br>
Poetry는 pip가 가지고 있는 약점을 보완해주는 package 관리자입니다. <br>
<i>poetry.lock</i> file을 통해 의존성 관리를 할 수 있으며, 가상 환경을 제공해 project별 packgage version을 관리할 수 있습니다. <br>

## How to install poetry

### Install python in Windows
Python은 아래 site에서 설치 가능합니다.<br>
- <https://www.python.org/downloads/>

Python 설치 완료 후에는 Windows 환경 변수에 python이 포함되어 있는지 확인해야 하며, 없다면 추가해줘야 합니다.<br>
<img src="https://user-images.githubusercontent.com/90759236/172505986-3d126a8a-7026-49e5-a533-7fb19bfae065.png" style="border: 1px solid grey; max-width: 70%; height: auto;"><br>

### Install poetry
1. Windows Powershell을 admin 권한으로 open합니다. <br>
<img src="https://user-images.githubusercontent.com/90759236/172506208-a56349fd-e049-4d92-9405-7aed627138ff.png" style="border: 1px solid grey; max-width: 70%; height: auto;"><br>

2. 아래 command로 poetry를 설치해줍니다.<br>
```powershell
(Invoke-WebRequest -Uri https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py -UseBasicParsing).Content | python -
```

3. 설치된 poetry에 대한 환경 변수를 setting해줍니다. <br>
<img src="https://user-images.githubusercontent.com/90759236/172506432-22053a3c-8440-4b9c-acea-1f240c4518fb.png" style="border: 1px solid grey; max-width: 70%; height: auto;"><br>

4. Poetry가 정상적으로 설치되었는지 확인합니다. <br>
```sh
$ poetry --version
Poetry version 1.1.13
```

### How to delete poetry
1. Windows Powershell을 admin 권한으로 open합니다. <br>
<img src="https://user-images.githubusercontent.com/90759236/172506208-a56349fd-e049-4d92-9405-7aed627138ff.png" style="border: 1px solid grey; max-width: 70%; height: auto;"><br>

2. 아래 command로 poetry를 삭제합니다.<br>
```powershell
(Invoke-WebRequest -Uri https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py --uninstall -UseBasicParsing).Content | python -
```

### Dependency package 추가
<i>poetry add</i> command를 이용해 필요한 package를 설치할 수 있습니다. <br>
```sh
poetry add 'package name'
```
위 command로 package를 설치하면 <i>poetry.lock</i> file과 <i>pyproject.toml</i>이 변경됩니다. 버전상 문제가 없다면 두 file을 commit해주면 됩니다. <br>

### Dependency package 설치
아래 command를 이용해 poetry.lock file에 있는 package들을 가상 환경에 설치할 수 있습니다. <br>
```
poetry install
```

## Referenece
- [About Poetry](https://spoqa.github.io/2019/08/09/brand-new-python-dependency-manager-poetry.html)
- [Virtual env with Poetry](https://velog.io/@hj8853/Poetry%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EC%97%AC-%EA%B0%80%EC%83%81%ED%99%98%EA%B2%BD-%EB%A7%8C%EB%93%A4%EA%B8%B0)
- [VScode Interpreter with Poetry](https://amazingguni.medium.com/python-poetry%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%EB%A5%BC-vscode%EC%97%90%EC%84%9C-%EA%B0%9C%EB%B0%9C%ED%95%A0-%EB%95%8C-interpreter%EB%A5%BC-%EC%9E%A1%EB%8A%94-%EB%B0%A9%EB%B2%95-e1806f093e6d)





