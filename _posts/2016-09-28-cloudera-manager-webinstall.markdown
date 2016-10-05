---
layout: post
title:  "Ubuntu 14.04LTS에서 클라우데라 구축하기(2)"
date:   2016-09-28 15:18:23 +0700
categories: [Cloudera]
---

이전 글에서는 Ubuntu14.04LTS 환경에서 Cloudera Manager Server 설치와 여러가지 환경설정을 보았다. 이번 글에서는 설치된 Server에 접속하여 Web UI에서 클러스터를 구축하는 법을 보도록 한다.

## References
+   <em>[https://github.com/biospin/BigBio/blob/master/part03/week01_160503/hadoop/cloudera_install.md](https://github.com/biospin/BigBio/blob/master/part03/week01_160503/hadoop/cloudera_install.md)</em> - 운영체제와 관련없이 겹치는 부분은 대부분 보고 그대로 적은 부분이 많습니다.


![Screenshot WebLogin](https://raw.githubusercontent.com/yangyangii/yangyangii.github.io/master/static/img/_posts/WebUI-Login.JPG  "Screenshot WebLogin")

## Web UI Login
+   초기 ID/PW는 admin/admin이다. 필요에 따라 변경해주면 되겠다.

+   각 서버의 호스트 이름은 번호를 ubuntu1, ubuntu2, ..., ubuntu9 등 넘버링으로 하면 관리하기 편하다.

+   클러스터를 구성하는 도메인명을 등록해야한다.


![Screenshot WebLogin](https://raw.githubusercontent.com/yangyangii/yangyangii.github.io/master/static/img/_posts/web1.JPG  "Screenshot WebLogin")
![Screenshot WebLogin](https://raw.githubusercontent.com/yangyangii/yangyangii.github.io/master/static/img/_posts/web2.JPG  "Screenshot WebLogin")
![Screenshot WebLogin](https://raw.githubusercontent.com/yangyangii/yangyangii.github.io/master/static/img/_posts/web3.JPG  "Screenshot WebLogin")
![Screenshot WebLogin](https://raw.githubusercontent.com/yangyangii/yangyangii.github.io/master/static/img/_posts/web4.JPG  "Screenshot WebLogin")
![Screenshot WebLogin](https://raw.githubusercontent.com/yangyangii/yangyangii.github.io/master/static/img/_posts/web5.JPG  "Screenshot WebLogin")

[jekyll-gh]: https://github.com/mojombo/jekyll
[jekyll]:    http://jekyllrb.com
