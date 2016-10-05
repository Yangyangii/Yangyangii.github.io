---
layout: post
title:  "Ubuntu 14.04LTS에서 클라우데라 구축하기(2)"
date:   2016-09-28 15:18:23 +0700
categories: [Cloudera]
---

이전 글에서는 Ubuntu14.04LTS 환경에서 Cloudera Manager Server 설치와 여러가지 환경설정을 보았다. 이번 글에서는 설치된 Server에 접속하여 Web UI에서 클러스터를 구축하는 법을 보도록 한다.

## References
+   <em>[https://github.com/biospin/BigBio/blob/master/part03/week01_160503/hadoop/cloudera_install.md](https://github.com/biospin/BigBio/blob/master/part03/week01_160503/hadoop/cloudera_install.md)</em> - 운영체제와 관련없이 겹치는 부분은 대부분 보고 그대로 적은 부분이 많습니다.

## Before Install
+   괜히 사용자 계정 써서 sudo 쓰고 다시 설정하고 하는 수고로움을 하지 말고 바로 root로 접속해서 하도록 한다.

+   각 서버의 호스트 이름은 번호를 ubuntu1, ubuntu2, ..., ubuntu9 등 넘버링으로 하면 관리하기 편하다.

+   클러스터를 구성하는 도메인명을 등록해야한다.


## Setting Network
Local Network Server를 사용하는 사람도 있을 것이고, AWS Server와 같은 Cloud Server를 사용하는 사람도 있을 것이다.

필자의 경우에는 학교에 Server를 두고 구축해야 했기에, Local Network Server를 기준으로 한다.

총 9대의 서버가 있으며, 스위치를 통해 각 네트워크를 연결하고 1번 서버를 호스트 서버로 통해서 종속된 서버들에 접속하기 위해 호스트 서버에만 외부 랜을 연결했고, 나머지 서버에는 Private IP를 설정하고 구축했다.


+   <em>DHCP Server</em> - 1번 서버에만 외부 랜이 연결되어 있으므로, 나머지 서버들이 1번 서버를 통해 인터넷이 가능하게 하기 위하여 1번 서버에서 DHCP Server를 가동해준다.

```
root@dlp:~# apt-get -y install isc-dhcp-server
root@dlp:~# vi /etc/dhcp/dhcpd.conf
# line 16: specify domain name
option domain-name "srv.world";
# line 17: specify nameserver's hostname or IP address
option domain-name-servers dlp.srv.world;
# line 24: uncomment
authoritative;
# add at the last
# specify network address and subnet-mask
subnet 192.168.0.0 netmask 255.255.255.0 {
     # specify default gateway
     option routers 192.168.0.1;
     # specify subnet-mask
     option subnet-mask 255.255.255.0;
     # specify the range of leased IP address
     range dynamic-bootp 192.168.0.1 192.168.0.254;
}
root@dlp:~# initctl start isc-dhcp-server 
isc-dhcp-server start/running, process 1852
```


![Screenshot WebLogin](https://raw.githubusercontent.com/yangyangii/yangyangii.github.io/master/static/img/_posts/WebUI-Login.JPG  "Screenshot WebLogin")


[jekyll-gh]: https://github.com/mojombo/jekyll
[jekyll]:    http://jekyllrb.com
