## GIT - Tips

### 리모트 저장소 변경

```bash
# 리모트 저장소 확인
$ git remote -v
origin    git@github.com:foundy/git-notes.git (fetch)
origin    git@github.com:foundy/git-notes.git (push)

# 리모트 저장소 변경
$ git remote set-url origin https://github.com/foundy/git-notes.git

# 리모트 저장소 변경 확인
$ git remote -v
origin    https://github.com/foundy/git-notes.git (fetch)
origin    https://github.com/foundy/git-notes.git (push)
```

### 이전 커밋의 author 변경

아래 예시는 마지막 커밋에 author를 변경하는 명령어이다.

```bash
$ git commit --amend --author "foundy <foundy@foundy.io>"
```

`rebase`를 사용하여 특정 커밋들을 수정 할 수도 있다. \(`rebase`까지 포함하면 내용이 길어져서 패스...\)

