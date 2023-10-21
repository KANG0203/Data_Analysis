## 2pg.

supervised learning
- e.g. classification, regression
- training data는 관측의 실제값을 나타내는 label과 함께 제공된다
- 새로운 데이터(unlabel)는 training set을 기반으로 에측 혹은 분류된다

unsupervised learing
- e.g. cluster
- training data의 label을 모른다
- data 기저 구조를 찾기 위해 사용된다

## 3pg.

classification
- target은 categorical or finite discrete이다.

Regression
- target은 연속적이다

## 4
Supervised learning process  

data preprocessing
- Data cleaning, integration, reduction, transformation

Training (learning model)
- 주어진 데이타를 training, validation, test set으로 나눈다.
- training set에서 learn, construct 한다

Validation (tuning model)
-  validation set에서 모델의 정확정을 평가한다
-  모델의 hyper-parameters 조정

Test and deploy(배포)
-  hyper-parameter values로 test set에서 모델의 정확성을 평가
-  배포하거나 미래를 예측한다 model로

## 8 pg.

model을 data에 정확히 fitting하는 것은 좋지 않다. -> overfitting  
10pg.보면 overfitting이 error가 더 큰 것을 볼 수 있다.  

## 11pg.

Bias-variance trade-off(편향 분산 분석)
- generalization error = variance + bias^2

## 13pg.

-  validation set에서 조정된 Hyperparameterssms valid set에 overfit될 수 있다
-  진짜 gerneralization error를 조사하기 위해 test set이 필요하다.

## 14pg.

Measures for classification and ranking
- Confusion matrix, Accuracy, F1-score, AUC, MAP, NDCG

Measures for regression
- MSE, RMSE, MAE, MAPE

뒤에 부분은 일단 pass
