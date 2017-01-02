---
layout: post
title:  "Statistics Summary with R"
date:   2017-01-02 17:18:23 +0700
categories: [Statistics]
---


## 통계에서 필요한 개념들 요약 정리
+   데이터 마이닝을 하는 데에 있어서 필요한 통계적 기법들이 있다. 그런 것들을 분석을 하는 데에 자주 사용하기 위해 정리하는 것이 좋을 것 같다.
+	R을 통해 실습을 하며 익히는 데에 있어서 그 의미를 파악하고 통찰력을 갖는 데에 필요한 것들을 위주로 정리한다.

Bernoulli distribution, Binomial distribution, Poisson distribution, Geometric distribution

Normal distribution, t distribution, chi-square distribution, F distribution


+	Bernoulli Distribution
시행횟수 1번이다.
Outcome이 0 또는 1만 가진다. 성공 혹은 실패.
성공확률 p로 나타내며, 실패확률은 q 혹은 (1-p)로 나타낸다.
E(X) = p 이며, V(X) = p(1-p) 이므로, p = 0.5일 때, 분산값이 가장 크다.
Denoted by X~Bernoulli(p)
Parameter 1개

+	Binomial Distribution
n번 던졌을 때... (즉, 몇번 던질지가 정해져 있다. n은 고정이다.)
E(X) = np, V(X) = np(1-p)
Denoted by X~Bin(n, p)
Parameter 2개
Bernoulli(p) 는 Binomial의 Special Case.(n=1일 때)
{% highlight ruby %}
> plot(seq(0,6,1), dbinom(seq(0,6,1), 6, 0.3), type='h', lwd=3)
{% endhighlight %}
![Screenshot Binomial](https://raw.githubusercontent.com/yangyangii/yangyangii.github.io/master/static/img/_posts/Statistics-Summary-withR-1.jpeg  "Screenshot Binomial")
{% highlight ruby %}
> plot(seq(0,6,1), dbinom(seq(0,6,1), 6, 0.5), type='h', lwd=3)
{% endhighlight %}
![Screenshot Binomial2](https://raw.githubusercontent.com/yangyangii/yangyangii.github.io/master/static/img/_posts/Statistics-Summary-withR-2.jpeg  "Screenshot Binomial2")

+	Poisson Distribution
단위시간에 일어나는 갯수
E(X) = lambda, Var(X) = lambda
포아송으로 할 경우, 평균과 분산이 같은지는 체크해 볼 필요가 있음.
Denoted by X~Poi(lambda)

+	Geometric Distribution
남아선호사상이 있을 때, 첫 아들이 나올 때까지 자녀를 낳는다고 해도, 남녀 비율은 1:1이다.
성공할 때까지 낳아야할 자녀의 수.(Setting)
그렇다면 남자 비율이 더 많은 이유는..?

+	Negative Distribution
k번 성공할 때까지의 횟수.
Geometric distribution은 Special case(k=1)

+	Normal Distribution
Denoted by X~N(μ, σ²)
표준 정규 분포
Z ~ N(0, 1)
μ 로부터 ±σ, ±2σ, ±3σ 범위 내에 확률변수 값이 포함된 확률은 각각 68.3%, 95.4%, 99.7% 이다.




{% highlight ruby %}
sudo vi /etc/spark/conf/log4j.properties

root.logger=INFO,console
-> root.logger=WARN,console
{% endhighlight %}