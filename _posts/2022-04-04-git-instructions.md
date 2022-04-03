---
layout: single
title: "[Git] git 사용법(git init, status, add, commit, push)"
categories: git
tags: [git, 2022/04/04]
toc: true
toc_sticky: true
author_profile: true
comments: true
share: true
related: true
published: true
sidebar: 
    nav: "docs"
---

## 1. 서론  

&nbsp;&nbsp;&nbsp;&nbsp;깃허브 블로그나 강의들을 통해 배우면서 작성한 코드들을 깃허브에 업로드하느라 요즘 GitHub Desktop을 자주 사용하고 있다. 하지만 Git bash를 통하여 명령어로 깃을 활용하는 방법도 배워보고 싶어져서 Git을 활용하는 방법들을 나름대로 정리해보려고 한다.

## 2. 본론  

### 1. 사전준비   

- [git-scm](https://git-scm.com/)에서 다운받아 설치한다.
- 아래와 같이 git bash를 이용하여 git 작업에 사용할 사용자 이름과 이메일(github 이메일)을 설정해준다. --global을 사용하여 설정하면 저장소별로 따로 설정할 필요 없이 한번만 하면 된다.
  
```
$ git config --global user.name "YOUR NAME"
$ git config --global user.email "YOUR EMAIL"
```

- 제대로 설정이 되었는지는 아래처럼 확인할 수 있다.

```
$ git config user.name
"YOUR NAME"
$ git config user.email
"YOUR EMAIL"
```

- 만약 위의 설정을 삭제하고 싶으면 아래처럼 하면 된다.

```
$ git config --global --unset user.name
$ git config --global --unset user.email
```

&nbsp;&nbsp;&nbsp;&nbsp;위의 설정을 통해 Github에서 git 커밋의 이메일 정보를 사용해 Github의 사용자를 매칭하는 원리이다.

### 2. 저장소 설정  

- 아래의 명령어를 통해 git 저장소를 만들 수 있다. git 저장소를 만들게 되면 해당 디렉토리 내에 .git 폴더(프로젝트와 버전 관리에 대한 정보가 담겨져 있는 폴더)가 생성된다.
  
```
$ git init
```  

### 3. git status 

<img alt="status" src="https://git-scm.com/book/en/v2/images/lifecycle.png" width=600>  

&nbsp;&nbsp;&nbsp;&nbsp;우선, 워킹 디렉토리의 모든 파일은 Tracked(관리대상) Untracked(관리대상 x)로 나누어진다. 그리고 Tracked file은 Unmodified, Modified, Staged 상태 세가지로 나누어진다. 이와 같은 상태는 git status 명령어를 통해 확인할 수 있다.  
  
-  Untracked
Git의 추적 관리가 이루어지지 않는 상태.

![Untracked](https://user-images.githubusercontent.com/97603503/161444627-b0c32141-ced4-4476-a6d7-a8d3a941cd33.png)

- Tracked(Staged)
git add를 통해 staging area(commit을 진행하기 전 임시 저장된 상태)에 올릴 수 있으며, git이 파일의 상태를 추적 관리하기 시작한다.

![Staged](https://user-images.githubusercontent.com/97603503/161444799-464ea037-6bfb-42e9-a2a7-0a0acf950698.png)

- Unmodified / Modified
git add를 하면 파일은 Tracked, Unmodified 상태가 된다. 그 후 파일을 수정하면 Modified 상태가 된다. 
그리고 git add를 통해 staging area에 있는 파일은 그 당시 파일을 복사한 것이기 때문에 한 파일이 아래의 사진과 같이 두가지 상태를 가질 수 있다.

![Modified](https://user-images.githubusercontent.com/97603503/161445036-c91e571b-2958-485f-b565-99fbe7fc3af9.png)  

### 4. git add  

- 위에서 언급했듯이 아래처럼 파일을 staging area로 보낼 수 있다.
  
```
$ git add "파일명"
```

- 하지만 파일을 하나하나 add 하기 귀찮을 경우 아래의 명령어들을 통해 한번에 처리할 수 있다. 

```
// 프로젝트 폴더 전체 파일 추가
$ git add - A

// 현재 폴더의 파일들 추가
$ git add .

```

- 만약 git add한 파일을 되돌리고 싶으면 아래의 명령어로 되돌릴 수 있다.

```
// 특정 파일 add 취소
$ git reset HEAD "파일명"
$ git restore --staged "파일명"

// 전체 파일 
$ git reset HEAD
```  

### 5. git commit 

- commit은 현재까지의 작업을 .git 파일에 기록 및 저장하는 것으로, 아래의 명령어를 통해 파일을 commit로 보낼 수 있다.
  
```
// 자세한 메시지와 함께 커밋, vim에서 메시지 작성
$ git commit

// add후 자세한 메시지와 함께 커밋, vim에서 메시지 작성
$ git commit -a

// 간단한 메시지와 함께 커밋
$ git commit -m "message"

// add후 간단한 메시지와 함께 커밋
$ git commit -am "message"
```  

- 만약 커밋을 취소하고 싶으면 아래의 명령어로 되돌릴 수 있다.

```
// 커밋을 취소하고, staged 상태로 보존
$ git reset --soft HEAD^

// 커밋을 취소하고, unstaged 상태로 보존
$ git reset HEAD^
```

### 6. git push 

- 커밋을 통해 로컬에 코드 변경 이력을 남긴 후, 원격 저장소에 전송하기 위해 git push를 사용한다.
  
```
// 처음 git push를 할 때
$ git push "저장소명" "브랜치명"

// 그 후
$ git push
```  

### 6. 에러  

- 아래와 같은 에러가 뜰 경우 ```rm -f ./.git/index.lock``` 명령어를 통해 해결할 수 있다.

```
fatal: Unable to create 'repository/.git/index.lock': File exists. 
If no other git process is currently running, this probably means a git process crashed in this repository earlier. 
Make sure no other git process is running and remove the file manually to continue.
```

```
fatal: Unable to create 'repository/.git/index.lock': File exists. 
Another git process seems to be running in this repository, e.g.an editor opened by 'git commit'. 
Please make sure all processes are terminated then try again. 
If it still fails, a git process may have crashed in this repository earlier: 
remove the file manually to continue.
```  

## 3. 결론  

&nbsp;&nbsp;&nbsp;&nbsp;막연히 어려울 것 같던 명령어를 통해 git을 활용하는 법이 포스팅을 작성하면서 몇번 실습해보니 생각처럼 어렵지 않았다. 마지막으로 글 쓸 당시 잔디 상태를 남기며 글을 마친다.

![github](https://user-images.githubusercontent.com/97603503/161447553-e0b8dde2-a8da-41ad-8562-6686084bb149.png)

## 4. 참고자료  

Ⅰ. [git 문서](https://git-scm.com/docs)  

---

```bash
이제 막 프로그래밍 공부를 시작한 초보 개발자입니다.
이 블로그 글들의 주 목적은 공부한것을 복습하기 위한것이며, 
만약 틀리거나 수정하면 좋을 부분들은
친절하게 댓글달아주시면 감사하겠습니다. :)
```

---