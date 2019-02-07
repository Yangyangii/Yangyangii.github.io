---
title:  "Jupyter Notebook 원격 서버 사용법 (ubuntu)"
tags:	Linux jupyter
article_header:
  type: cover
  image:
    src: "/assets/instacode.png"
---

# Jupyter notebook 원격 서버 사용법
## 목적
- 랩실에 들어온 친구들이 자꾸 물어본다. 4학년도 물어본다. 3학년도 물어본다. 몇년째 반복중ㅋㅋㅋㅋㅋ. 이걸 보도록 하자.

## 설치

- Anaconda 3.7 (3.6 downgrade 권장)
    - 최근에는 tensorflow gpu 나 pytorch gpu 를 conda 를 통해 설치하면, cudnn 과 같은 별개의 작업을 필요로 하지 않는다. 그러므로 docker 를 이용하거나 커스터마이징이 필요한 build 에 자신 있는 고수가 아니라면 그냥 아나콘다를 사용하기를 권장한다. 웬만해서는 최적화가 더 잘 되어있다.

    - 글의 주 목적인 Jupyter notebook 라이브러리는 Anaconda 설치 시에 포함되어 있다. 최신버젼이 필요한 것이 아니면 따로 설치하지 말자.

    - Anaconda 설치와 환경변수 설정 등은 알아서 하자. 설치할 때 root를 건들지 말자.(물론 sudo 권한이 없을 확률이 높을 것이다) user로 깔도록 하자.

## 원격 서버

- 강력한 GPU를 가진 서버에서 딥러닝 학습을 하고 싶은데, 아직 관련 프로그래밍이 익숙하지 않아 GUI도 지원하고 interactive coding이 가능한 Jupyter notebook을 쓰고 싶다.

- jupyter notebook 의 초기 설정을 해줄 필요가 있다. 먼저 비밀번호를 사용하기위해 미리 파이썬에서 암호를 생성하고 생성된 sha1 뭐시기를 복사한다.

{% highlight ruby %}
from notebook.auth import passwd
passwd()
Enter password: ....
Verify password: ....
'sha1:...............'
{% endhighlight %}

- user home 으로 가서 다음과 같은 명령어를 입력한다.

{% highlight ruby %}
user@server:~$ jupyter notebook --generate-config
user@server:~$ vi .jupyter/jupyter_notebook_config.py
{% endhighlight %}

- 파일을 열었으면, 다음 키워드들을 찾아서 주석해제 후에 수정해준다. 암호는 아까 복사한거 붙여넣기.

- port는 기본으로 8888을 사용하는데, 서버는 보통 여러명이서 같이 사용하니 중복되지 않도록 그냥 나만의 포트를 설정하자. 하다 못해 netstat 으로 열려있는 포트라도 확인하고 작업하자.

- ip는 저대로 쓰지 말고 서버 ip를 쓰면 된다.

{% highlight ruby %}
c = get_config()
c.NotebookApp.open_browser = False
c.NotebookApp.password = u'sha1:...'
c.NotebookApp.ip = '192.168.0.1'
c.NotebookApp.port = 12345
{% endhighlight %}

- 저장하고 나온 후에, user home에서 다음과 같이 입력하자.

{% highlight %}
user@server:~$ screen -S jupy
user@server:~$ jupyter notebook
{% endhighlight %}

- Ctrl + a + d 를 클릭한 후 screen session 에서 빠져나온다.

- 자세한 screen 사용법은 구글링을 하도록 하자.

- 이제 원격 서버에 접속 가능한 내부망에서 브라우저를 열고 ip:port 를 입력하면 된다.

## 끝
- 끝