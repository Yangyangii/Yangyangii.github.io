---
layout: post
title:  "윈도우즈에서 TensorFlow 설치"
date:   2017-12-28 15:18:23 +0700
author: Jin
categories: TensorFlow
tags:	TensorFlow Python Anaconda
cover:  "/assets/instacode.png"
---

## 설치 목록
+	Anaconda(python3.6)
+	TensorFlow 1.4(CPU Version)


## Anaconda Install
+	[Anaconda_64bit-Download](https://repo.continuum.io/archive/Anaconda3-5.0.1-Windows-x86_64.exe)
+	[Anaconda_32bit-Download](https://repo.continuum.io/archive/Anaconda3-5.0.1-Windows-x86.exe)
+	혹시 본인 OS가 32bit라면 해당 버전을 다운받으면 된다.
+	설치 시에는 Default 설정대로 모두 Next를 하면 된다.(다른 환경의 파이썬을 동시에 사용하는게 아니라면 Add Anaconda to my PATH environment variable 체크 권장)


## Tensorflow Install
+	Anaconda 설치가 끝나고나면 윈도우 시작 메뉴에서 anaconda라고 검색한다.
+	Anaconda Prompt 실행
{% highlight ruby %}
c:\> conda create -n tensorflow
c:\> activate tensorflow
(tensorflow) c:\> pip install --ignore-installed --upgrade tensorflow
{% endhighlight %}
+	되도록이면 네트워크가 느리지 않은 곳에서 하길 바란다. 실패할 가능성이 있음.
+	기존에 다른 Python이 설치되어 있을 경우, 미리 제거하거나 환경변수를 삭제하길 권장한다. 충돌이 일어날 수 있음.
+	다른 Python을 사용할 일이 없는 경우, anaconda environment 없이 마지막 텐서플로우 설치 명령어만 사용해도 무관하다.


## Test
+	TensorFlow 설치가 끝나면 다음과 같이 테스트를 진행한다.
{% highlight ruby %}
(tensorflow) c:\> python
>>> import tensorflow as tf
>>> hello = tf.constant('Hello, TensorFlow!')
>>> sess = tf.Session()
>>> print(sess.run(hello))
{% endhighlight %}


## Jupyter Notebook
+	Jupyter Notebook을 사용하여 실습시간에 프로그래밍할 예정이므로 잘 작동하는지 확인 바랍니다.
{% highlight ruby %}
(tensorflow) c:\> jupyter notebook
{% endhighlight %}
+	위 명령어 입력 후 브라우저에 뜨면 New > Python3 로 노트북파일 생성.
+	위의 Tensorflow test 다시 테스트.
![Screenshot Jupyter](https://raw.githubusercontent.com/yangyangii/yangyangii.github.io/master/assets/_posts/Jupyter-Notebook.JPG  "Screenshot Jupyter")
![Screenshot Jupyter](https://raw.githubusercontent.com/yangyangii/yangyangii.github.io/master/assets/_posts/Jupyter-test.JPG  "Screenshot Jupyter")


## References
+   <em>[https://www.tensorflow.org/install/install_windows#installing_with_anaconda](https://www.tensorflow.org/install/install_windows#installing_with_anaconda)</em>
+	<em>[https://www.tensorflow.org/install/install_mac#installing_with_anaconda](https://www.tensorflow.org/install/install_mac#installing_with_anaconda)</em>
+	<em>[https://www.anaconda.com/download/](https://www.anaconda.com/download/)</em>

## Trouble Shooting
+	맥 유저도 거의 동일하게 설치하며 단 아나콘다 버젼은 레퍼런스에서 맥버전으로 다운받아야함. 자세한 내용은 reference 참고.
