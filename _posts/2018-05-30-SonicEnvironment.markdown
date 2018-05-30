---
layout: post
title:  "openai gym-retro 환경 구축(with Sonic)"
date:   2018-05-30 19:00:00 +0700
author: Jin
categories: Reinforcement_Learning
tags:	Reinforcement_Learning Sonic gym-retro
cover:  "/assets/instacode.png"
---

## OS environment
+	Ubuntu 17.10LTS, Python3.6(Anaconda)

## gym-retro
+	openai gym에 이어 SEGA game을 추가하고 보강한 gym-retro가 나왔다.
+	gym도 많은 이들이 환경구축에서 좌절하는데... 더 어려워졌다!
+	환경구축에서 해야할 일이 추가된 점은 Steam을 설치하고 인증하고 다운받는 것 정도이다.
+	pip install gym-retro 를 이용해 설치하는 경우 ROM이 정상적으로 설치되지 않는다.
+	gym-retro github의 최신버젼 코드를 확인하면 ROM 설치하는 코드에서 다소 다른 점이 있는데, 버그를 fix한 것으로 보인다. 그에 맞춰서 코드를 수정해줄 필요가 있다.
+	스팀 설치 파일은 <em>[Link](https://store.steampowered.com/about/)</em>를 통해 받아준다.
+	정상적인 스팀 설치를 위해서는 sudo apt-get install curl python-apt zenity 를 통해 3가지 패키지를 설치한다.
+	sudo dpkg -i steam.deb 를 통해 설치
+	스팀 설치 후에 ROM 복사 전에 apt-get install lib32gcc1 를 할 필요가 있다.
+	python -m retro.import.sega_classics 를 통해 스팀에 접속 ROM 다운 및 설치
+	아이디, 비밀번호, 스팀가드 입력
+	스팀가드가 처음에 모르면 아무거나 입력하고, 메일로 전송받는다.(해당 컴퓨터에서 처음 접속시 메일로 스팀가드 전송됨)
+	위의 순서를 잘 따랐다면 설치 완료.
+	python에서 아래 코드를 실행해보고 잘되면 완료.


import retro
env = retro.make(game='SonicTheHedgehog-Genesis', state='GreenHillZone.Act1')


## References
+   <em>[정원석님 블로그](https://wonseokjung.github.io//openairetro/update/Retro-1/)</em>
+	<em>[openai retro details](https://contest.openai.com/details)</em>