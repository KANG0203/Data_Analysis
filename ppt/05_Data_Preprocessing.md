Data Preprocessing -> 데이터 전처리 : 데이터를 원하는 형태로 변형하여 분석  

## 5pg ~ 7pg.

Data cleaning
- incomplete, Noisy, inconsistent, intentional

incomplete or missing
- tuple 무시
- miss data 넣기
- fill in autimatically
- missing val 다루는 모델 사용

Noisy data
- do smmothing
- remove automatically
- remove manually(수동)
- do nothing

## 9pg.

Sampling  

representative subset of data를 선택하려면
- random sampling
- sampling without replacement (모집단에서 제거)
- Sampling with replacement (모집단에서 제거 안함)
- Stratified sampling(계층별 셈플링)

## 10pg.

Micro-clustering
- data를 많은 작은 그룹으로 나누고, 각 그룹을 repersentative point로 대체

## 11pg.

Dimensionality reduction
- linear transformation, PCA
- nonlinear transformation, tSNE

## 12pg.

t-sne와 umap는 nonlinear demensional reduction, data의 상대적인 거리를 유지하며 축소  

SNE와 UMAP의 차이:
(1) tSNE는 무작위 초기 지점에서 시작하고, UMAP은 이미 계산된 지점에서 시작합니다.
(2) tSNE는 각 반복에서 모든 지점을 이동시키는 반면, UMAP은 지점의 하위 집합을 이동시킵니다.
(3) UMAP은 클러스터의 수를 제어하는 하이퍼파라미터인 이웃의 수를 가지고 있습니다.

## 13pg ~ 15pg.

Feature slection (attribute subset selection)
- redundant(중복) or irrelevant attribute(관련없는 속성)을 감지하고 제거

Heuristic search
- d 속성에서 2^d의 가능한 속성 subset
- forward : 반복적으로 좋은거 추가
- backward : 반복적으로 나쁜거 추가

15는 걍 보자  

## 16pg.

Sensitivity analysis
- 각 특징 값을 변겨하고, 결과에 얼마나 영향 미치는지 보자.

Gradient-based methods for neural network
- 각 인스턴스의 특징에 대한 그래디언트를 계산하고 평균을 구함

Ensemble methods
- 정보 획득 및 노드가 담당하는 인스턴스 수를 기반으로 계산

## 18pg.

Data transformation

One-hot encoding - categorical/nominal 변수를 one-hot 백터로 전환  
integer encoding - ordinal 변수를 integer로 전환  
Normalization - numeric column을 common scale로 전환  
Discretization - continouou value를 discrete value로 전환

