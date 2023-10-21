## 2pg.

KDD(knowledge discovery and data mining) process  
이번 시간에 배우는 EDA는 data understanding part이다.  

## 3pg.

슥 읽어보자.  

## 4pg ~ 5pg.

앞에서 봤었다.  

## 6pg.

Exploratory data Analysis(EDA)
- statistical graphics나 다른 data visualization mode를 이용하여 데이터 집합의 주요 특성을 요약하는 데이터 분석 접근 방식
- Univariate analysis : histogram, boxplot
- Multivariate analysis : scatter plot, correlation analysis, heatmap
- Dimenstional reduction : PCA tSNE

## 7pg.

Measuring the central tendency  

Mean
- sample 평균과 population 평균의 차이를 알자.
- Weighted arithmetic mean(가중 평균) : 가중치 곱해서 평균 구하기
- Trimmed mean : 극단적 값 제외하고 평균 내기

Median
- 홀수이면 중간값, 짝수이면 가운데 값 평균

Mode
- 최빈값, 즉 가장 많이 나온 값
- Empirical formula(실험식?)  mean-mode = 3 * (mean-median)

## 8pg.

Symmentric(대칭)
- Mean, median, mode 가 같다.

skewed data
- positively는 왼쪽으로 치우쳐저 있어서, Mode < Median < Mean이다.
- negatively는 오른쪽으로 치우쳐저 있어서 Mean < Median < Mode이다.

## 9pg.

distributive measure
- 데이터를 작은 부분 집합으로 분할하여 계산(sum, count)

algebraic measure
- 하나 이상의 distributive measure에 함수를 적용하여 계산.(mean = sum/count)

holistic measure
- 전체 데이터 셋을 계산(median)

## 10pg.

Measuring the dispersion of data  

Quartile(분위수)
- Q1 : 1/4, Q3 : 3/4
- IQR = Q3 - Q1
- min Q1 median(Q2) Q3 max
- boxplot 그릴때 위에 것들 그림

분산 표준편차 구하는 식 보기. (이 둘은 algebraic measure이다)  

## 11pg.

Boxplot
- median은 box 안에 선으로 표시
- 박스 처음이 Q1, 끝이 Q3, 높이는 IQR
- Whiskers : max min을  box 밖에 line으로 표시
- Outliers: max/min 밖에 point로 표시

## 12pg.

대충 읽자  

## 13pg.

Histogram
- 값의 분포 보여줌
- 두 히스토그램이 min, Q1, median, Q3, and max 이 같을 수 있지만 그림이 다를 수 있다.

## 14pg.

Kernel density estimation(KDE)
- histogram을 스무스하게

## 15pg.

Heat map
- 2-d나 3-d임. value를 color로 보여줌

## 16pg.

q-quantiles
- 값을 동일한 size의 q subset으로 나눔
  
Quantile plot  
- data x를 오름차순으로 정렬한다. fi는 100 * f% 의 data가 x와 거의 동일한 것을 나타냄.
- 뭔 개소리?

## 17pg.
Q-Q plot
- 한가지 그래프의 분위수를 다른 그래프의 분위수에 대해 나타냄

## 18pg.

scatter plot - 슥 보기  

## 19pg ~ 20pg.

Covariance(공분산)
- 두 데이터의 분산, 계산 방법 보기

양수면 positively correlated, 음수면 negative correlated, 0이면 independent

## 21pg ~ 23pg.

R (correlation coefficient) and R-squared
- R^2은 두 변수의 관계로 설명되는 변화의 백분위
- R^2은 correlation의 direction을 나타내지 않는다

뒤에 예시 보기

## 24pg.

X^2(chi-square) test
- 공식이나 보자.

## 25pg.

Similarity
- objects가 더 비슷할수록 값이 크다.
- 일반적으로 0~1 임

Dissimilarity(distance)
- 더 비슷할수록 작다
- 최소는 0이고, 상한값은 다양하다

Proximity refers to a similarity or dissimilarity  

## 26pg.

Proximity measure for nominal attributes  

![image](https://github.com/KANG0203/Data_Analysis/assets/144585363/72b5bf84-25f0-427d-b99a-af3c217a7b65)

대충 그림 보고 이해  

## 27 ~ 28pg.

Proximity measure for binary attributes
- 대충 식 보자
- 걍 표에서 둘다 1, 1과 0, 0과1, 0과0 인 개수 세서 대입하면 된다

## 29pg.

distance matrix 이거 26pg에서 계산하던거다.  

## 31pg.

Distance on numeric data: Minkowski distance
- h에 따라 거리 구하는 방식 달라진다.
- supermum은 걍 x거리 y거리 구해서 더 큰 놈이다.


##
뒤에 걸러 슈벌
