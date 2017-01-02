---
layout: post
title:  "Statistics Summary with R(2)"
date:   2017-01-02 17:18:23 +0700
categories: [Statistics]
---


## 통계에서 필요한 개념들 요약 정리
+   데이터 마이닝을 하는 데에 있어서 필요한 통계적 기법들이 있다. 그런 것들을 분석을 하는 데에 자주 사용하기 위해 정리하는 것이 좋을 것 같다.
+	R을 통해 실습을 하며 익히는 데에 있어서 그 의미를 파악하고 통찰력을 갖는 데에 필요한 것들을 위주로 정리한다.

Sampling, Central Limit Theorem, t distribution, chi-square distribution, F distribution


+	Sampling Distribution
표본들의 평균은 모집단의 평균이다.
μx̄ = μ
실제 생활에서는 모집단의 정보를 알아내기 위해 표본집단의 정보를 사용하고 이를 위해 통계가 쓰인다.


+	Central Limit Theorem
모집단이 Normal이면 표본도 Normal
모집단이 Normal이 아니어도, N이 충분히 크면(N>=30) approximately Normal
Example)
{% highlight ruby %}
> hist(rbinom(10000, 1, 0.9), breaks = c(-0.5,0.5,1.5), freq=F, xlab='x', main='Bernoulli(0.9)')
{% endhighlight %}
![Screenshot CentralLimitTheorem](https://raw.githubusercontent.com/yangyangii/yangyangii.github.io/master/static/img/_posts/Statistics-Summary-withR-4.jpeg  "Screenshot CentralLimitTheorem")
{% highlight ruby %}
> x <- numeric()
> for (i in 1:10000) x <- c(x, mean(rbinom(50,1,0.9)))
> hist(x, freq = F, main='n=50')
{% endhighlight %}
![Screenshot CentralLimitTheorem2](https://raw.githubusercontent.com/yangyangii/yangyangii.github.io/master/static/img/_posts/Statistics-Summary-withR-5.jpeg  "Screenshot CentralLimitTheorem2")


+	Hypothesis Testing
p-value, test statistic, t-value
H0 : μ = 0
H1 : μ ≠ 0
-> 양측 검정.
H0 : μ = 0
H1 : μ > 0 or H1 : μ < 0
-> 단측 검정.

Steps of Hypothesis Testing
1. Build hypothesis
2. Set significance level
3. Determine test statistic
4. Collect data
5. Calculate test statistic
6. Make conclusion

