---
published: true
title: "[GitHub] Draft Pull Request"
date: 2022-06-17
last_modified_at: 2022-06-17T12:53:00
toc: true
toc_sticky: true
categories:
  - github
tags:
  - github
  - pull request
  - pr
  - draft pull request
---

## Draft Pull Request
GitHub에서는 Draft Pull Request라는 기능을 제공합니다. <br>
일반적인 개발 flow는 아래와 같습니다.<br>
* <b> Branch 생성(feature branch)->code 작성 및 수정-><u>PR open</u>->Reviewer가 PR review->Merge </b>

위 flow에서 PR open시 일반 Pull Request가 아닌 <b>Draft Pull Request</b>를 선택할 수 있습니다. <br><br>
Draft Pull Request는 현재 개발이 진행 중(In progress)을 tag하는 Pull Request입니다. <br>
해당 PR은 merge 버튼이 비활성화 되어있으며, PR status를 "Ready for review"로 변경해야 draft 상태가 아닌 일반 PR로 변경됩니다.
<br><br>

### Example - Create draft pull request
1. 특정 branch를 만들어 작업(commit->push)을 진행 후 GitHub Web에서 PR을 open합니다. <br>
<img src="https://user-images.githubusercontent.com/90759236/174212148-de2fdad8-9e2e-4c8e-a695-3d2c2ce98375.png" style="border: 1px solid grey; max-width: 80%; height: auto;"><br>

2. Pull Request message 작성 후 아래 "Create pull request" 버튼 옆 화살표 버튼을 눌러 "Create draft pull request"를 선택합니다. <br>
<img src="https://user-images.githubusercontent.com/90759236/174212843-e589abb3-0355-44e4-9879-bdea3b1219b1.png" style="border: 1px solid grey; max-width: 80%; height: auto;"><br>

3. "Draft pull request" 버튼을 선택합니다. <br>
<img src="https://user-images.githubusercontent.com/90759236/174213141-7738b5bb-1816-4670-8181-09836152c942.png" style="border: 1px solid grey; max-width: 80%; height: auto;"><br>

4. 아래처럼 merge가 막혀있는 것을 알 수 있으며, 일반 PR로 변경하려면 "Ready for review"를 선택하면 됩니다. <br>
<img src="https://user-images.githubusercontent.com/90759236/174217322-0f9f12de-eb53-45cc-96e8-e2c4c65e6d09.png" style="border: 1px solid grey; max-width: 80%; height: auto;"><br>
<br>

## Reference
* [GitHub Blog](https://github.blog/2019-02-14-introducing-draft-pull-requests/)