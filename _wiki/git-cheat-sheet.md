---
layout  : wiki
title   : 
summary : 
date    : 2024-02-16 19:45:53 +0900
updated : 2024-02-17 17:12:50 +0900
tag     : 
toc     : true
public  : true
parent  : [[Git]]
latex   : false
---
* TOC
{:toc}

![image](https://camo.githubusercontent.com/572ed67739c1c5d83a618f39b77038477bb313e89ff841fca6670fd58632be16/68747470733a2f2f6a6473616c61726f2e636f6d2f5f696d616765732f67697474696d65776f726b666c6f772e706e67)

## 세 가지 상태

![image](https://git-scm.com/book/en/v2/images/areas.png)

### Committed

- 데이터가 로컬 데이터베이스에 안전하게 저장됨

### Modified

- 수정한 파일을 아직 로컬 데이터베이스에 커밋하지 않음

### Staged

- 현재 수정한 파일을 곧 커밋할 것이라고 표시한 상태


## Git 저장소 만들기

### init

```zsh
# 기존 디렉토리를 깃 저장소로 만든다.
$ git init
```

### clone

```zsh
# 기존 저장소(remote repository)에서 가져온다.
$ git clone https://github.com/pennynd1me/adsd.git
```

## Workspace

Local checkout, working copy, working tree.

### add

```zsh
# 워크스페이스 상의 변경 내용을 스테이징 영역에 추가한다.
$ git add .
```

### rm / mv

```zsh
# Tracked 상태의 파일을 삭제한 후(Staging Area에서 삭제) add
$ git rm [file]

# Tracked 상태의 파일을 rename한 후 Staging area로 add
$ git mv [file]
```


## Stash

작업중인 변경 사항을 일시적으로 저장해두고, 디렉토리를 clean한 상태로 만들어준다.

```zsh
# 변경 사항을 저장한다.
$ git stash

# 저장된 stash 목록을 확인한다.
$ git stash list

# 저장된 사항을 불러온다.
$ git stash apply

# 저장된 사항을 삭제한다.
$ git stash drop

# 마지막 항목을 불러와 적용한 후 삭제한다.
$ git stash pop
```


## Index (Staging Area)

### commit

```zsh
# 커밋 메시지를 한줄로 입력
$ git commit -m "messages"

# 마지막 커밋 수정
$ git commit --amend
```

### restore

```zsh
# 커밋하지 않은 변경사항 되돌리기
# 기존에는 git checkout -- [file]로 사용했지만 명확하지 않다는 문제가 있어 
# switch와 restore로 분리되었다.

# --staged
$ git restore --staged [file]
```


## Local Repository

### push

```zsh
# 로컬 저장소의 변경 사항을 원격 저장소로 업로드한다.
$ git push <remote_name> <branch_name>

$ git push origin main

# -u 옵션으로 upstream 브랜치를 설정할 수 있다.
# 로컬의 main 브랜치를 upstream의 main에 연결한다.
$ git push -u origin main
```

### reset

```zsh
# 원하는 시점으로 돌아간 뒤 이후 내역(히스토리)들을 지운다.
# --soft 옵션으로 staging area 까지만 되돌린다
$ git reset --soft <commit_hash>

# --hard 옵션으로 workspace 까지 되돌린다
$ git reset --hard
```

### branch

```zsh
# 브랜치 목록을 보여준다.
$ git branch

# 지정한 브랜치를 생성한다.
$ git branch <branch>

# 지정한 브랜치를 삭제한다.
$ git branch -d <branch>
```

### switch

```zsh
# 지정한 브랜치로 전환한다.
$ git switch <branch_name>

# 브랜치를 새로 만들며 전환한다.
$ git switch -C <branch_name>
```

### checkout

```zsh
# 브랜치 전환 후 restore 한다. (switch와 restore를 합친 명령어)
$ git checkout <branch_name>

# 새로운 브랜치 생성 후 전환, restore한다.
$ git checkout -b <new_branch_name>
```

### merge

```zsh
# 두 개 브랜치를 한 커밋에 이어붙인다.
$ git merge <sub_branch>

# 충돌이 발생할 시 중단
$ git merge --abort

# --squash 옵션으로 분기된 이후 커밋들을 하나의 커밋으로 만들 수 있다.
$ git merge --squash

# 브랜치가 분기된 이후 새로운 커밋이 올라오지 않았다면 up-to-date 이므로
# 그 변경 이력을 그대로 main으로 가져올 수 있다. (fast-forward)

# 분기된 이후 새로운 커밋이 올라왔다면 분기된 브랜치와 main 브랜치를
# 공통 부모로 한 새로운 merge commit을 생성한다. (recursive)
$ git merge --no-ff
```

### rebase

```zsh
# 브랜치를 다른 브랜치에 이어붙인다. (base를 다시 설정)
# HEAD가 target branch에서 base branch로 향해야한다.
$ git switch <target_branch>
$ git rebase <base_branch>

# 다른 토픽 브랜치에서 갈라져 나온 브랜치를 이어붙인다.
$ git rebase --onto <new_base> <old_base>
```

### cherry-pick

```zsh
# 다른 브랜치의 특정 커밋을 현재 브랜치로 가져온다.
$ git cherry-pick <commit_hash>

$ git switch <branch_name>
$ git cherry-pick <commit_hash>
```

### revert

```zsh
# 특정 커밋의 변경 사항을 되돌리는 새로운 커밋을 생성한다.
# 변경 사항을 삭제하지 않고 이전 상태로 되돌릴 수 있다.
$ git revert <commit_hash>
```

## Remote Repository

### pull

```zsh
# 원격 저장소의 변경 사항을 가져와 로컬 저장소의 현재 브랜치에 병합한다.
# 내부적으로 fetch해 merge 또는 rebase를 사용해 병합한다.
$ git pull <remote_repo/branch>
```

### fetch

```zsh
# 원격 저장소의 변경 사항을 가져온다.
# 가져온 변경 사항은 로컬 저장소의 원격 브랜치에 저장된다.
$ git fetch <remote_repo>
```

## General

### config

```zsh
# 전역 설정 관리
$ git config --global <key> <value>

# 로컬 설정 관리
$ git config --local <key> <value>

# 시스템 설정 관리
$ git config --system <key> <value>

# 설정 확인
$ git config <key>

# .gitconfig 파일을 수정해 Alias 설정도 할 수 있다.
$ git config --global alias.* <value>
$ vim ~/.gitconfig
```

### status

![image](https://git-scm.com/book/en/v2/images/lifecycle.png)
출처: [https://git-scm.com/book/en/v2](https://git-scm.com/book/en/v2/images/lifecycle.png)

- 인덱스 파일과 현재 HEAD 커밋의 차이 (Changes to be committed)
- 워크스페이스와 인덱스파일과의 차이 (Changes not staged for commit)
- Git에 의해 추적되지 않는 파일(Untracked files)을 표시한다.

```zsh
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	new file:   _wiki/Vim.md
	new file:   _wiki/vim-tutorial.md

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   _wiki/index.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	_wiki/git-cheat-sheet.md
```


### diff

```zsh

# 워크스페이스와 스테이징 영역을 비교해 차이점을 보여준다.
$ git diff

# 스테이징 영역과 최신 커밋을 비교한다.
$ git diff --staged

# 두 개의 커밋을 비교한다.
$ git diff <commit_hash1> <commit_hash2>

# 디렉토리나 파일의 변경 사항을 비교한다.
$ git diff <directory_name>
$ git diff <file_path> or <file_name>
```

### log

```zsh
# 커밋 히스토리를 조회한다
$ git log

# --graph 그래프 표현
# --decorate 모든 레퍼런스 표시
$ git log --color --graph --decorate --date=format:'%y-%m-%d' --pretty=format:'%C(cyan)%h%C(auto)%d %s %C(magenta) (%ad)%C(bold blue) %an'
```

![imgae](https://github.com/pennynd1me/pennynd1me.github.io/assets/75344410/829c116a-1152-4a5c-bd4f-a0db7d62ee22)

- 이 블로그의 기반을 만들어주신 종립님의 커밋 log를 참고

### HEAD와 checkout

`HEAD`: 현재 작업중인 브랜치의 가장 최신 커밋을 가리키는 포인터. 현재 작업 디렉토리에서 작업 중인 브랜치의 끝 부분.

- 커밋: 작업 중인 브랜치의 가장 최신 커밋, 새로운 커밋을 만들면 HEAD가 이동하여 새로운 커밋을 가리킨다.
- 브랜치: HEAD가 특정 브랜치를 가리키는 경우, 작업 디렉토리에서의 변경 사항은 해당 브랜치에 추가된다.
- 태그: HEAD가 특정 브랜치를 가리키는 경우, 특정 커밋을 가리키는 고정된 위치가 된다.

```zsh
# checkout (#^ 또는 ~개수만큼 이전으로 이동 HEAD^^^, HEAD~5)
$ git checkout HEAD^

# 커밋 해시를 이용해 이동
$ git checkout <commit_hash>

# 원격 저장소의 브랜치로 이동할 때도 checkout을 사용
$ git checkout <remote_repo/branch>
```

### remote

```zsh
# 원격 저장소 목록 보기
$ git remote -v

# 원격 저장소 추가하기
$ git remote add <remote_name> <repo_url>

# 삭제하기
$ git remote remove <remote_name>

# 이름 변경하기
$ git remote rename <old_name> <new_name>

# 원격 저장소 URL 변경하기
$ git remote set-url <remote_name> <new_url>
```


## 추가로 알아야할 것들

- flog
- interactive option
- blame
- tag
- bisect
- alias


## 참고
- [https://git-scm.com/docs](https://git-scm.com/docs)
- [https://ndpsoftware.com/git-cheatsheet.html#loc=stash](https://ndpsoftware.com/git-cheatsheet.html#loc=stash)
- [https://stackoverflow.com/questions/3689838/whats-the-difference-between-head-working-tree-and-index-in-git](https://stackoverflow.com/questions/3689838/whats-the-difference-between-head-working-tree-and-index-in-git)
- [https://velog.io/@oneny/git-초보자인-나를-위한-git-cheat-sheet-만들기](https://velog.io/@oneny/git-초보자인-나를-위한-git-cheat-sheet-만들기)
- [https://pers0n4.io/github-remote-repository-and-upstream/#fn-1](https://pers0n4.io/github-remote-repository-and-upstream/#fn-1)
- [https://blog.outsider.ne.kr/1505](https://blog.outsider.ne.kr/1505)
- [https://meetup.nhncloud.com/posts/122](https://meetup.nhncloud.com/posts/122)
