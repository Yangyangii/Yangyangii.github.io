---
layout: post
title:  "Statistics Summary with R(4)"
date:   2017-01-03 17:18:23 +0700
categories: [Statistics]
---


## 통계에서 필요한 개념들 요약 정리
+   데이터 마이닝을 하는 데에 있어서 필요한 통계적 기법들이 있다. 그런 것들을 분석을 하는 데에 자주 사용하기 위해 정리하는 것이 좋을 것 같다.
+	R을 통해 실습을 하도록 하고, 의미를 파악하고 통찰력을 갖는 데에 필요한 것들을 위주로 통계 개념을 정리한다.

- Topic: Simple Linear Regression

+	Simple Linear Regression
Y를 X값으로 예측하는 기법이다.
X를 Y로 예측하려면 식을 바꿔줘야한다. Regression은 Symmetric이 아니다.
대체로 Ordinary Least Square(OLS) 추정 방법으로 오차의 제곱의 합을 최소화하는 기법을 사용한다.
Coefficient of Determination: 평균과 비교했을 때 예측치가 실제값에 얼마나 가까운지를 나타내는 것으로 클수록 좋다. 일반적으로 R-square로 나타낸다. 하지만 이것이 모델의 예측 성능을 나타내지는 않는다.(overfitting의 가능성도 있으며, test 데이터로 측정해봐야 한다)
아래 그림에서 SSR/SST로 계산하며, 실제로 Correlation Coefficient(r²)를 나타낸다.
![Screenshot RSquare](https://raw.githubusercontent.com/yangyangii/yangyangii.github.io/master/static/img/_posts/R-square.jpeg  "Screenshot RSquare")
Example)
linear model(lm) library를 사용해서 Simple Linear Regression을 실습해본다.
{% highlight rhtml %}
> library(MASS)
> lm.fit = lm(medv~lstat, data = Boston)
> summary(lm.fit)

Call:
lm(formula = medv ~ lstat, data = Boston)

Residuals:
    Min      1Q  Median      3Q     Max 
-15.168  -3.990  -1.318   2.034  24.500 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept) 34.55384    0.56263   61.41   <2e-16 ***
lstat       -0.95005    0.03873  -24.53   <2e-16 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 6.216 on 504 degrees of freedom
Multiple R-squared:  0.5441,	Adjusted R-squared:  0.5432 
F-statistic: 601.6 on 1 and 504 DF,  p-value: < 2.2e-16
{% endhighlight %}
t value는 Estimate / Std.Error 이며, Pr(>|t|)는 p-value를 나타낸다.
p-value가 0에 가까우므로 유의하다고 볼 수 있다.
Residual standard error는 여러 잔차의 차이? Multiple일 때 쓰임.
Multiple R-squared는 y를 x가 54% 정도 대변해준다는 뜻이다.
F-test는 simple에서 t-test와 동일하다. 506 row이므로 자유도는 504.
F-statistic == t-value²

{% highlight rhtml %}
> with(Boston, plot(lstat, medv, pch="♥", main='Graph'))
> abline(lm.fit, lwd=4, col='red')
> abline(coef(lm.fit)[1], coef(lm.fit)[2], col="blue", lwd=2)
{% endhighlight %}
실제로 두 Column에 대해 plot을 그려보면 Correlation이 높아보이며, Simple Linear Regression에 대해 잘 대변해주는 Line이 그려지는 것을 확인할 수 있다. coef()를 통해 함수가 정상적으로 적용됐는지 확인할 수 있다.
![Screenshot Simple-Linear-Regression](https://raw.githubusercontent.com/yangyangii/yangyangii.github.io/master/static/img/_posts/Simple-Linear-Regression.jpeg  "Screenshot Simple-Linear-Regression")


+	Multiple Linear Regression
여러 독립변수 X1, X2, ..., Xn에 대하여 종속변수 Y를 구하는 기법이다.
R에서 아래와같이 사용가능하다. step()의 경우에는 multiple linear Regression에서 변수를 어떻게 선정하느냐에 따라 더 좋은 성능이 나오는지 판단해주는 함수이다.
{% highlight rhtml %}
> three.fit <- lm(medv ~ crim + zn + indus, Boston)
> all.fit <- lm(medv ~ ., Boston)
> summary(myfit)
> stepfit <- step(myfit)
{% endhighlight %}
종속변수를 parameter에 넣을때 .은 모든 Column을 가리킨다.
하지만 변수선정 함수를 사용하지 않아도 분석에 있어서 Scatter Plot을 통해서 직관적으로 보고 판단하는 방법도 가능하다.
이외에도 lm.beta, car의 vif, lmtest, leaps 등의 라이브러리로 테스트하고 변수를 선별하는 작업들이 가능하다.
