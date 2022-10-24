---
published: true
title: "[VSCode] python에서 "module_name" could not be resolved 해결 방법"
date: 2022-10-24
last_modified_at: 2022-10-24T12:38:00
toc: true
toc_sticky: true
categories:
  - vscode
tags:
  - vscode
  - python
  - could not be resolved
---

* <b>작성일</b>: 2022/10/24

## VSCode에서 python 개발 시 "Could not be resolved" 해결 방법
VSCode에서 python 개발 시 이미 설치한 모듈(pip를 이용해)인데도 <b>"[module name] Colud not be resolved"</b> error가 발생할 수 있습니다. <br>
이는 가상 환경에서 개발 시, 혹은 여러 python version이 설치되어 있을 때 VSCode가 적절한 interpreter(python version) 경로 를 매칭하지 못해서 생기는 문제로, 현재 개발 환경에 맞는 python version을 설정해주면 해결됩니다. <br>
<br>
Interpreter? C언어나 Java의 Compiler와 달리 소스 코드를 처음부터 한 라인씩 순차적으로 해석하며 실행하는 프로그램 <br>

<br>

### Python interpreter 설정 방법
1. VSCode에서 <u>Ctrl + Shift + p</u> 입력<br>
<img width="445" alt="image" src="https://user-images.githubusercontent.com/90759236/197444598-e583cebc-f8f8-4c16-93df-05341dd406ae.png" style="border: 1px solid grey;"> <br>

2. "<b><u>Python: Select Interpreter</u></b>" 선택<br>

3. 본인의 개발환경에 맞는 Python version 및 경로 선택<br>
<img width="445" alt="image" src="https://user-images.githubusercontent.com/90759236/197444832-cdc89c5a-c049-4b17-b96e-cb09162fd7ad.png" style="border: 1px solid grey;"> <br>
