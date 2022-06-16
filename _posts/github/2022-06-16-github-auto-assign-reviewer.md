---
published: true
title: "[GitHub] github action으로 reviewer 자동 할당하기"
date: 2022-06-16
last_modified_at: 2022-06-16T09:32:00
toc: true
toc_sticky: true
categories:
  - github
tags:
  - github
  - github action
  - auto-assign-action
  - reviewer
---

## GitHub action을 이용한 reviewer 자동 할당
회사에서 개발 진행 시 reviewer가 정해져 있는 상황에서 PR(pull request) open후 매번 reviewer를 등록하는 것도 매우 귀찮은 일입니다. <br>
이에 PR 관련 event 발생 시(일반적으로 open할 때 trigger합니다), 자동으로 reviewer를 등록해주는 <b>auto-assign-action</b>이라는 action이 있습니다. <br>

### auto-assign-action
<b>auto-assign-action</b>은 PR 요청이 열릴 때 PR에 reviewer를 추가하는 action입니다. <br> 사용 방법은 아래와 같습니다. <br>

1. <i>.github/workflows</i> folder에 아래의 action yml file을 추가해줍니다. File 이름은 상관 없습니다.

    ```yml
    name: 'Auto Assign Reviewer'
    on:
      pull_request:
        types: [opened, ready_for_review]

    jobs:
      add-reviews:
        runs-on: ubuntu-latest
        steps:
          - uses: kentaro-m/auto-assign-action@v1.2.1
            with:
              configuration-path: '.github/some_name_for_configs.yml' # Only needed if you use something other than .github/auto_assign.yml
    ```
    
    * <i>ready_for_review</i>는 Draft Pull Request가 일반 Pull Request로 변경되었을 때의 activity입니다. 저의 경우 draft pull request를 사용할 일이 없어 'opened'와 'reopened' type을 걸어놨습니다.
    * <i>configuration-path</i>는 아래 2번에 있는 yml file name이 <i>auto_assign.yml</i>이 아닌 경우에 셋팅하며, <i>auto_assign.yml</i>인 경우에는 설정할 필요 없습니다.

2. <i>.github</i> folder에 아래의 <i>auto-assign.yml</i> file을 만듭니다. 

    ```yml
    # auto-assign.yml
    
    # Set to true to add reviewers to pull requests
    addReviewers: [true/false]

    # Set to true to add assignees to pull requests
    addAssignees: [true/false/author]

    # A list of reviewers to be added to pull requests (GitHub user name)
    reviewers:
      - reviewerA
      - reviewerB
      - reviewerC

    # A number of reviewers added to the pull request
    # Set 0 to add all the reviewers (default: 0)
    numberOfReviewers: 0
    # A list of assignees, overrides reviewers if set
    # assignees:
    #  - assigneeA

    # A number of assignees to add to the pull request
    # Set to 0 to add all of the assignees.
    # Uses numberOfReviewers if unset.
    # numberOfAssignees: 2

    # A list of keywords to be skipped the process that add reviewers if pull requests include it
    # skipKeywords:
    #   - wip
    ```

    * <i>addReviewers</i>나 <i>addAssignees</i>는 원하는 값(true, false, ...)를 골라주면 됩니다. 대괄호("[", "]")는 삭제하시기 바랍니다.
    * <i>reviewers</i>는 GitHub user name을 입력해줍니다.
    * <i>numberOfReviewers</i>가 0인 경우 <i>reviewers</i>에 등록한 모든 유저가 reviewer로 등록됩니다. 당연한 얘기지만 본인은 제외됩니다.
    * <i>addAssignees</i>에서 <b>'author'</b>를 선택하면 PR을 open한 user가 assignee로 할당됩니다.


### Multiple Reviewers list
Reviewer group이 여러 개라면 아래처럼 auto-assign.yml을 변경할 수 있습니다.

```yml
# Set to true to add reviewers to pull requests
addReviewers: true

# Set to true to add assignees to pull requests
addAssignees: false

# A number of reviewers added to the pull request
# Set 0 to add all the reviewers (default: 0)
numberOfReviewers: 1

# A number of assignees to add to the pull request
# Set to 0 to add all of the assignees.
# Uses numberOfReviewers if unset.
# numberOfAssignees: 2

# Set to true to add reviewers from different groups to pull requests
useReviewGroups: true

# A list of reviewers, split into different groups, to be added to pull requests (GitHub user name)
reviewGroups:
  groupA:
    - reviewerA
    - reviewerB
    - reviewerC
  groupB:
    - reviewerD
    - reviewerE
    - reviewerF

# Set to true to add assignees from different groups to pull requests
useAssigneeGroups: false
# A list of assignees, split into different froups, to be added to pull requests (GitHub user name)
# assigneeGroups:
#   groupA:
#     - assigneeA
#     - assigneeB
#     - assigneeC
#   groupB:
#     - assigneeD
#     - assigneeE
#     - assigneeF

# A list of keywords to be skipped the process that add reviewers if pull requests include it
# skipKeywords:
#   - wip
```


## Reference
[auto-assign-action github repo](https://github.com/kentaro-m/auto-assign-action)