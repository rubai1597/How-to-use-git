# 간단한 git 사용법

* [여기](https://medium.com/@psychet_learn)를 참고하였습니다.



## 1. Set up for Git

Git은 software이기 때문에 자신의 운영체제에 맞는 Git을 설치해야한다.

### 1.1 For Windows

Windows에서 git을 사용하기 위해서는 [Git 공식홈페이지](https://git-scm.com/downloads)에서 다운로드 받는 것이 가장 좋다. 설치가 완료되면 Git Bash(or cmd)를 통해 여러가지 git 명령어를 입력할 수 있다.

### 1.2 For Ubuntu

> \> sudo apt-get install git

위 코드를 terminal에 입력하면 번거로운 과정 없이 설치할 수 있다.



## 2. Local repository 만들기

Git repository는 remote repository와 local repository로 나뉜다. remote repository는 여러 사람이 함께 공유하는 저장소이고 local repository는 내 개인 PC에 저장되어 있는 전용 저장소이다. 여러 사람이 동시에 작업하는 경우 충돌을 방지하기 위해 주로 remote repository에 있는 내용을 local repository에 복사한 후에 local repository에서 내용을 수정하는 방식으로 작업을 진행한다.

[Github](https://github.com)에 이미 remote repository가 있다고 가정을 하고 local repository를 만들어 보자.

우선 remote repository의 파일들을 복사해오기 위한 directory를 따로 만든다.

> \> mkdir <폴더 이름>
>
> \> cd <폴더 이름>
>
> ex)
>
> mkdir test
>
> cd test

다른 repository와 헷갈리지 않도록 remote repository와 이름을 동일하게(혹은 비슷하게) 하는 것이 좋다. 폴더를 만든 후에는 cd 명령어를 통해 그 directory로 이동한다.

### 2.1 Git 초기화 하기

Git을 사용하기 위해서는 반드시 초기화를 해줘야한다. 초기화는 다음 명령어를 통해 간단히 시켜줄 수 있다.

> \> git init

이 명령어를 입력하고 나면 현재 directory에 .git이라는 폴더가 생성되는데 여기에는 Git에 대한 여러가지 정보가 담겨져있다.

### 2.2 Git 계정 설정

이제 사용자 설정을 하여 git에 접근이 가능하도록 해야한다. 다음 명령어를 통해 사용자를 설정해준다. user.email에는 자신이 가입했던 github의 이메일을 사용한다.

> \> git config user.name <사용자 이름>
>
> \> git config user.email <사용자 이메일>
>
> ex)
>
> git config user.name "rubai1597"
>
> git config user.email "rubai1597@naver.com"

### 2.3 Git 가져오기

Github에 이미 프로젝트가 생성되어 있다면 'clone'이라는 명령어를 통해 repository에 있는 파일들을 local로 가져올 수 있다.

> \> git clone <URL.git>
>
> ex)
>
> git clone https://github.com/rubai1597/test

git clone을 하게 되면 repository에 있던 파일들이 현재 directory에 생성되는 것을 확인할 수 있다. (사실 git clone을 하게 되면 git init까지 자동으로 설정된다.)

## 3. Git update 하기

### 3.1 Repository URL설정

local repository에서 수정된 내용을 remote로 update하기 위해서는 repository의 URL을 설정해줘야한다.

> \> git remote -v

git remote -v 명령어를 현재 설정되어 있는 repository의 URL을 나타낸다. 설정되어 있는 repository가 없다면 "`not a git repository (or any of the parent directories)`" 라고 error가 발생할 것이다.

만약 설정된 repository가 없다면 다음의 명령어를 통해 remote repository를 추가시켜준다.

> \> git remote add <저장소 이름> <URL.git>
>
> ex)
>
> git remote add origin https://github.com/rubai1597/test

설정을 하고 다시 한번 git remote -v를 입력해주면 다음과 같이 repository를 확인할 수 있다.

><저장소 이름> <URL.git> (fetch)
>
><저장소 이름> <URL.git> (push)
>
>ex)
>
>origin  https://github.com/rubai1597/test.git (fetch)                           
>origin  https://github.com/rubai1597/test.git (push)

URL을 잘 못 추가하여 수정하고 싶다면 다음의 명령어들을 사용하여 변경하거나 제거할 수 있다.

> \> git remote delete <저장소 이름>		# 저장소 URL 삭제
>
> \> git set-url <저장소 이름> <URL.git>	# 저장소 URL 수정

### 3.2 수정된 내용 Update

local repository에서 내용이 수정되었는지 기억이 나지 않는다면 다음의 명령어를 통해 확인할 수 있다.

> \> git status

git status 명령어를 local과 remote에 있는 내용이 얼마나 다른지를 알려주는 명령어이다. 아직까지는 수정한 내용이 없기 때문에 "`No Commits yet`"이라고만 나올 것이다.