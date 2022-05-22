---
name: CONTRIBUTING
about: contributing to this project
title: ''
labels: documentation
assignees: ''

---

# Contributing
이 프로젝트에 참여하기 위한 방법.

## Issue tracker 사용하기
이 채널에 만들어져있는 bug reports, feature requests, submitting pull requests template을 사용하여 작성해주세요.

## 코딩 규칙
1. 들여쓰기: space 4를 기준
2. HTML: scss 컴포넌트 단위로 하여 해당 html 요소에 시작과 끝에 이런 식으로 작성
```
<!-- accout: 계좌 정보 -->
<div class="account">
</div>
<!-- end: account -->
```

## Commit Convention (prefix)
- feat: Add server.py
- fix: Fix Typo server.py
- docs: Add README.md, LICENSE
- conf: Create .env, .gitignore, dockerfile
- BREAKING CHANGE: Drop Support /api/v1
- refactor: Refactor user classes

### Pull Requests 
#### 주의 사항
1. 불필요한 commit 요청을 하지 않도록 합니다.
2. pull request를 하기 이전에 충분히 코드를 정리하여 최종적인 경우에만 사용합니다.
3. 프로젝트에서 사용되는 코딩 규칙 (들여쓰기, 주석 등), 요구사항을 준수합니다.

#### 진행 순서
1. Fork > Clone > remote 환경설정
- Fork: 현재 프로젝트 
- Clone: 자신이 fork한 팀장의 repo를 자신의 local에 clone합니다.
- configure remote: 팀장의 repo를 pull받아 최신으로 유지하기 위해 remote 설정을 합니다.(upstream-owner: 팀장)
```
# Clone your fork of the repo into the current directory
git clone https://github.com/<your-username>/<repo-name>
# Navigate to the newly cloned directory
cd <repo-name>
# Assign the original repo to a remote called "upstream"
git remote add upstream https://github.com/<upstream-owner>/<repo-name>
```

2.  clone을 한 뒤 `main branch`만 있을텐데 `git flow init`을 통해서 `develope branch`를 생성합니다.

3. `develop branch`는 기능이 모여지는 공간이다. 그래서 `git flow feature start 기능명`를 통해 기능에 대한 branch를 생성합니다.

4. Issue탭을 확인하여 지시 받은 기능 구현 및 수정을 확인합니다.

5. `git status`로 자신의 상태를 확인하고 `git add 파일명` and `git commit`을 한다. `commit`할 때 **prefix**와 **commmit메시지**를 신경써서 작성합니다.

6. 기능 추가를 완료했으면 `git flow feature finish 기능명`를 입력합니다.
- 이때, `Merge Commit`이 자동으로 생성됩니다.(`feature branch`에서 > `develop branch`로 Merge되는 것을 요청 하는 commit)
  - 만약 그 기능이 `ISSUE #1` 이었다면 `Merge Commit`에서 `solve #1`이라고 commit 메시지를 남겨야합니다.

7. 마무리 단계에서 `git push - u origin develop`을 입력합니다.

8. 또한, 기능 추가를 완료했으면 반드시 ISSUE에서 체크박스에 체크합니다. 그래야지 다른 팀원들도 확인이 가능합니다.

9. Contribue 버튼에 `open pull request` 또는 초록버튼 `Compare & pull request`를 누릅니다.
- request 보낼 때 **팀원 repository에서 > 팀장 repository로 보내는 것. 주의! 이때 branch는 'develop'. main 아닙니다! 주의!**
- title에는 '기능명과 한 일을 간략히 작성.', comment에는 `close #1` (해당 issue가 #1 이라면)
- 이후 `Create pull request`.

10. request 페이지에서 '초록색'이면 `merge 가능`한 상태, '회색'이면 `conflict 상태`.
- `conflict`가 발생했을 때 팀원이 코드를 고쳐서 다시 request.

11. `pull request`를 보낸 이후 팀장이 코드 리뷰를 하면서 `comment`를 달았다면 요청사항을 확인
- 먼저 확인했다는 `comment`를 다시 보내줍니다.
- 그리고 코드를 수정합니다.
  - `git status, git add 파일명, git commit`. (commit message 신경)
  - `git push origin develop`을 하면 그 팀원이 작업했던 내역 아래에 이어서 붙습니다.(request 페이지에서)

12. `git remote -v`를 해서 upstream이 있는지 확인.

13. 팀장(repo-owner)의 최신 코드를 `pull`받아 올 수 있게 `upstream`으로 설정.
```
git switch <dev-branch>
git pull upstream <dev-branch>

// git pull upstream develop
```

**주의**: commit message, Issue 체크 등을 신경써서 작업합니다.
