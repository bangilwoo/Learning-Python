---
title: Pycham으로 git 연동하기 
--- 

## 1. 준비하기 

연동을 하기에 앞서서 github회원가입과 git, Pycharm을 설치해야 한다. 

- [github](https://github.com/) 회원가입
 - 서버에 접속 후 가입을 진행한다.
- [Pycham](https://www.jetbrains.com/ko-kr/pycharm/) 다운로드
- [git](https://git-scm.com/downloads) 다운로드
 - Pycham, git 링크로 접속해 설치를 한다.

## 2. 실행하기(연동)

설치가 완료 되었으면 Pycharm을 실행하자.

![](../image/1.jpg)

- 창이 열리면 Get from Version Control을 클릭한다.

![](../image/2.png)

- URL에 회원가입한 github의 프로젝트파일 URL을 붙여 넣는다.

위의 URL을 기입하는 곳에 본인의 github 프로젝트를 기입하기에 앞서 github내의 프로젝트를 만들어보자

![](../image/3.jpg)

- 로그인을 하게 되면 위와 같은 메뉴가 나올 것이다. 그러면 "Repositories"를 클릭한다.

![](../image/4.jpg)

- 초록색 버튼의 "new" 클릭한다.

![](../image/5.jpg)

- 만들려고 하는 프로젝트 명을 입력한다. 테스트를 위해 test로 설정했다. 이름을 설정했다면 아래의 초록색버튼 "Create repository"를 클릭하여 프로젝트를 생성한다.

![](../image/6.jpg)

- 프로젝트가 생성 됐다면 프로젝트의 URL을 복사한다.

![](../image/7.jpg)  

- 복사한 URL을 위의 그림과 같이 붙여 넣고 파란색버튼 "clone"를 클릭하여 생성한다. # 생성하기 전에 경로(Directory)를 지정해주자. 테스트를 위해 바탕화면에 생성하였다.

![](../image/8.png) 

- 생성하면 위와 같이 프로그램이 실행되고 지정한 경로로 파일이 생기면 Pycharm에 git허브가 연동 된것이다. 
