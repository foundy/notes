## GIT - Shortcuts

* [`$ git checkout -`](#-git-checkout--)
* [`$ git push origin :feature/mybranch`](#-git-push-origin-featuremybranch)
* [`$ git add -u`](#-git-add--u)
* [`$ git fetch -p`](#-git-fetch--p)

### `$ git checkout -`

* 이전 브랜치로 체크아웃
* `$ git checkout @{-1}`과 동일

### `$ git push origin :feature/mybranch`

* 리모트 브랜치 삭제
* `$ git push origin --delete feature/mybranch`와 동일

### `$ git add -u`

* _tracked files_ 전체를 stage로 추가한다.
* 주로 _untracked files_를 제외한 나머지 모두 stage로 올릴때 사용한다.
* `$ git add --update`와 동일
* 참고: [https://git-scm.com/docs/git-add\#git-add---update](https://git-scm.com/docs/git-add#git-add---update)

### `$ git fetch -p`

* 리모트 브랜치에 삭제된 내역을 로컬에 업데이트
* `$ git branch -a`하여 로컬에 출력되는 `remotes`를 살펴보면 원격지와 sync되지 않은 부분을 확인 할 수 있다.
* `$git fetch --prune`, `$ git remote prune origin`과 동일
