# git
> Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.

* [git-scm.com](https://git-scm.com)
* [github.com/git/git](https://github.com/git/git)

## Table of Contents
* [리모트 저장소 변경](#리모트-저장소-변경)
* [이전 커밋의 author 변경](#이전-커밋의-author-변경)

## Shortcuts
* [`$ git checkout -`](#-git-checkout--)

## Reference
* [GitHub/GIT CHEAT SHEET](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf)
* [Pro GIT](https://git-scm.com/doc)
* [Pro GIT](https://git-scm.com/book/ko/v2) (한글)
* [github/gitignore](https://github.com/github/gitignore) 유용한 gitignore 템플릿 모음
* [gitignore.io](https://www.gitignore.io) gitignore 템플릿 생성

---
## Table of Contents

### 리모트 저장소 변경

```bash
# 리모트 저장소 확인
$ git remote -v
origin	git@github.com:foundy/git-notes.git (fetch)
origin	git@github.com:foundy/git-notes.git (push)

# 리모트 저장소 변경
$ git remote set-url origin https://github.com/foundy/git-notes.git

# 리모트 저장소 변경 확인
$ git remote -v
origin	https://github.com/foundy/git-notes.git (fetch)
origin	https://github.com/foundy/git-notes.git (push)
```

### 이전 커밋의 author 변경

아래 예시는 마지막 커밋에 author를 변경하는 명령어이다.

```bash
$ git commit --amend --author "foundy <foundy@foundy.io>"
```

`rebase`를 사용하여 특정 커밋들을 수정 할 수도 있다. (`rebase`까지 포함하면 내용이 길어져서 패스...)

---

## Shortcuts

### `$ git checkout -`
- 이전 브랜치로 체크아웃
- `$ git checkout @{-1}`과 동일

### `$ git push origin :feature/mybranch`
- 리모트 브랜치 삭제
- `$ git push origin --delete feature/mybranch`와 동일

### `$ git add -u`
- *tracked files* 전체를 stage로 추가한다.
- 주로 *untracked files*를 제외한 나머지 모두 stage로 올릴때 사용한다.
- `$ git add --update`와 동일
- 참고: https://git-scm.com/docs/git-add#git-add---update

### `$ git fetch -p`
- 리모트 브랜치에 삭제된 내역을 로컬에 업데이트
- `$ git branch -a`하여 로컬에 출력되는 `remotes`를 살펴보면 원격지와 sync되지 않은 부분을 확인 할 수 있다.
- `$git fetch --prune`, `$ git remote prune origin`과 동일
