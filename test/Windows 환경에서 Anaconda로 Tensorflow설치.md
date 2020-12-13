## Windows 환경에서 Anaconda로 Tensorflow설치
---

anaconda를 설치하고, 쥬피터 노트북에서 작업을 하는데 **No module named ‘tensorflow**’ 에러가 발생하면, tensorflow를 실행할 수 없다.

이러한 문제를 해결하기 위해서는 Anaconda에 tensorflow패키지를 설치해야 오류없이 실행된다. 그래서 패키지 설치하는 방법을 알아보고자 한다.

Anaconda를 이용해 Tensorflow를 다운받고 실행해보자!!

다운 받기에 앞서 Anaconda Promapt를 관리자 권한으로 실행한다.(Windoow는 관리자 권한으로 실행해야 오류 발생이 없다) 실행창을 열었으면 명령어를 입력해 보자!

1) 경로 설정하기

Anaconda Promaps를 실행하면 경로가 anacoda가 아닌 다른 곳으로 설정되 있을수 있다.이 경로를 anaconda가 설치된 경로로 지정해 주자.(경로가 잘못 설정되면 패키지가 설치되지 않음)

![기존경로](../image/W A T/ten1.png)

위와 같이 경로가 다르게 지정되면 anaconda가 설치된 경로로 변경해줘야 한다.

![변경경로](../image/W A T/ten2.png)

2) 최신의 버전으로 업데이트 하기

```
> python -m pip install --upgrade pip
```

버전이 낮다면 위의 명령어를 실행하여 업데이트 하자!!

3) TensorFlow 설치하기

```
> activate tensorflow
```

패키지를 설치 했다면 쥬피터 노트북을 다시 실행 후 파일을 재 실행해보자!!


```python

```
