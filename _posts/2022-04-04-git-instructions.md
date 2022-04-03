---
layout: single
title: "[Git] git 사용법?"
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
  
```
1. Untracked
Git의 추적 관리가 이루어지지 않는 상태.
```

![Untracked](https://user-images.githubusercontent.com/97603503/161444627-b0c32141-ced4-4476-a6d7-a8d3a941cd33.png)

```
2. Tracked
git add를 통해 staging area(commit을 진행하기 전 임시 저장된 상태)에 올릴 수 있으며, git이 파일의 상태를 추적 관리하기 시작한다.
```

![Staged](https://user-images.githubusercontent.com/97603503/161444799-464ea037-6bfb-42e9-a2a7-0a0acf950698.png)

```
3. Modified
git add를 한 후 파일을 수정하면 Modified 상태가 된다. 
그리고 git add를 통해 staging area에 있는 파일은 그 당시 파일을 복사한 것이기 때문에 한 파일이 아래의 사진과 같이 두가지 상태를 가질 수 있다.
```

![Modified](https://user-images.githubusercontent.com/97603503/161445036-c91e571b-2958-485f-b565-99fbe7fc3af9.png)

4. Modified
수정한 파일을 아직 로컬 데이터베이스에 저장하지 않은 상태
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



git rm --cached <fileName>

## 3. 결론  

&nbsp;&nbsp;&nbsp;&nbsp;이번 포스팅에서는 형상관리도구, 특히 Git과 Github를 중심으로 궁금한 점들을 알아보았다. 취업준비 과정과 취업 후에도 활발하게 사용할 가능성이 큰 앱인만큼, 궁금한점이 생기면 새로운 포스팅을 통해 견문을 넓혀가보려고 한다. 마지막으로 조금은 뿌듯한 내 잔디를 보면서 포스팅을 마친다.

![github](https://user-images.githubusercontent.com/97603503/158716763-64397053-f50f-4226-95e2-83d96dd280a6.png)

## 4. 참고자료  

Ⅰ. [깃허브-위키백과](https://ko.wikipedia.org/wiki/%EA%B9%83%ED%97%88%EB%B8%8C)  

---

```bash
이제 막 프로그래밍 공부를 시작한 초보 개발자입니다.
이 블로그 글들의 주 목적은 공부한것을 복습하기 위한것이며, 
만약 틀리거나 수정하면 좋을 부분들은
친절하게 댓글달아주시면 감사하겠습니다. :)
```

---