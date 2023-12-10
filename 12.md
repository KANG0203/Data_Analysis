## 2pg.

cluster
- data object의 collection
- same group에서는 similar, other grops들은 dissimilar

clustering
- similar data를 cluter로 grouping, unsupervised learning
- data 분포에 대한 통찰을 얻고, 알고리즘을 실행하기 전 전처리 위해 쓰임

## 3pg.

High intra-class similarity: cohesive within clusters  
Low inter-class similarity: distinctive between clusters  

Similarity or distance metric
- 거리 함수의 정의는 interval-scaled, boolean, categorical, ordinal ratio, and vector variables과 같은 type에 따라 다르다.
- weight(가중치)는 application, data semantic를 고려해 다양한 변수와 관련시켜야 한다.

## 4pg.

Considerations for clustering
- partitioning 기준 - 단일 level vs (multi level) hierarchical clustering
- cluster 분류 - exclusive vs non-exclusive(각 object가 여러 cluster에 속할 수 있음)
- similarity measure - distance based vs connectivity based
- clusering space - full space(일반적으로 낮은 차원) vs subspace(일반적으로 고차원 clustering)
- constraints based clustering - constraints는 사용자 혹은 domain에 의해 제공될 수 있음.
- clustering shape and size - spherical shape and equivalent size(k-mean), arbitary shape and inequivalent size(DBSCAN)
- 점진적 clustering and input order에 대한 insensitivity

## 5pg.

partitioning approach
- 다양한 partition을 만들고, 그들을 특정 기준으로 평가한다. (ex> minimizing the sum of square errors)
- k-means, k-medoids

Hierarchical approach
- 계층적 cluster 생성
- Agglomerative clustering (AGNES), Diana, BIRCH, CAMELEON

Density-based approach
- connectivity or density 기반
- DBSCAN, OPTICS, DenClue

Grid-based approach
- grid나 feature space 기반
- STING, WaveCluster, CLIQUE

Model-based
- 각 cluster에 대해 model이 가설화되고, 해당 모델의 최적 적합을 찾는다
- EM, SOM, COBWEB

User-guided or constraint-based
- user-specified or application-specific constraints을 고려하여 clustering
- COD (obstacles), constrained clustering

Link-based clustering
- object는 종종 다양한 방식으로 linked된다.
- SimRank, LinkClus

# 7pg.

Partitioning methods - m object를 k clusters로 sum of distances를 최소화하는 방향으로 paritioning한다.  

k-means - 각 cluster는 cluster의 중심으로 나타낼 수 있다.  
k-medoids or PAM - 각 cluster는 cluster 내의 object 중 하나로 나타낼 수 있다.
k-modes  - categorical data에 대한 clustering

## 8 ~ 9pg.

K-means clustering  

algorithms
- 1. randomly K개의 중심점 설정
  2. 각 z를 가장 가까운 centroid에 할당
  3. 각 cluster의 평균 point로 centroids 계산
  4. centroids가 변하지 않을 때까지 2부터 반복
 
예시를 보면 각 D에서 가까운 c에 대한 cluster로 z를 설정하고, 각 cluster별로 평균 centroid를 계산하여 반복하는 것을 볼 수 있다.  

거리 함수가 필요하다
- domain knowledge를 반영하여 신중히 결정
- categorical data에 대해 means가 modes로 대체(k-modes)

local optima 찾기
- 초기 centroids에 따라 결과가 달라진다.
- 고급 heruristics ex> k-means++ -> 초기 값 설정해줌

Need to specify K
- 어떻게 K를 조절할까? 모든 K에 대해 loss를 계산하고 loss가 급격히 감소하는 지점을 찾는다.

Cluster shape
- spherical shape - not proper for non-convex shape clusters
- equivalent size - 비대칭 cluster에 적합 안함.

## 10pg.

PAM(k-medoids)
- means는 meadian보다 outliers에 민감하다.
- PAM은 가장 중앙에 위치한 object를 reference point로 사용하고, 나머지는 동일하다.
- central points를 계산하려면 data를 추가로 scan해야 한다.
- 계산 오버해드를 줄이기 위해 제안된 모델 ->  CLARA, CLARANS

## 12pg.

Hierarchical methods
- input으로 cluster의 개수가 필요하지 않다.

## 13 ~ 14pg.

Agglomerative clustering (AGNES)
- 반복적으로 가장 유사한 nodes를 merge하고, 모든 nodes가 하나의 cluster로 합쳐질 때까지 반복한다.

Divisive clustering (DIANA)
- 모든 노드에 대한 single cluster에서 시작하여, 모든 node가 하나의 cluster를 가질 때까지 반복한다.

## 15pg.

Dentrogram - a tree of clusters  
data objects의 clustering은 원하는 level에서 dendrogram을 자르면 얻을 수 있다.  

## 16pg.

Distance measure between clusters
- single link - 한 cluster의 elem과 다른 cluster의 elem 간의 가장 작은 거리
- complete link - 가장 큰 거리
- average - 평균 거리
- Centroid -  두 cluster의 중심점 간의 거리
-  Medoid - 두 클러스터의 medoid 간의 거

## 17pg.

Major weakness of hierarchical clustering method
- 이전에 수행된 작업을 취소할 수 없다.
- 확장성 부족 - 최소 시간 복잡도 O(n^2)

Advanced hierarchical clustering methods
- Birch - cf-tree를 사용하고 sub-cluster의 quality를 incrementally하게 조절
- Chameleon - dynamic modeling을 사용한 hierarchical clustering

## 19pg.

Density-based clustering features
- 임의의 모양의 cluster 발견
- noise를 잘 처리
- 최대 한번의 data scan 필요
- 종료 조건으로 density parameter가 필요

## 20pg.

Two parameters
- eps - neighborhodd의 최대 반경
- minpts - esp 내의 최소 points 수

Neps(p) - eps 내의 points 수  
core point - 반경 내의 poins가 Minpts보다 많은 poins  

Directly density-reachable
- q가 Neps(p)에 속하고 p가 core point인 경우, q는 p에서 Directly density-reachable이다.

Density-reachable
- q1,...,qn 에서 q1 = p이고 qn = q인데, qi+1에 qi에서 diresctly density reachable이면, q는 p에서 density-reachable이다.

Density-connected
- point 0에 대해 p와 q가 둘다 0에서 density reachable이면 q와 p는 density connected이다.

이해 잘 안가면 그림 보면 바로 이해감  

## 21pg.

DBSCAN: Density-based spatial clustering of applications with noise
- cluster는 density-connected point의 최대 집합으로 정의
- 임의의 shape의 cluster를 발견한다.
- outliers는 어느 cluster에도 density-connected되지 않는다.

Algorithm
- 임의의 p를 선택
- p에 대해 density-reachable한 모든 점을 검색한다.
- p가 core point면 cluster는 형성된다.
- 아니면, density-reachable이 없는 것이므로 다음 point 방문
- 모든 point가 진행 될까지 진행한다.

## 22pg.

그림을 보면 eps에 따라 clustering이 달라지는 것을 볼 수 있다.  

## 23pg.

OPTICS
- clustering structure를 구별하기 위해 point를 ordering
- density가 다양한 데이터에서 의미있는 clusters를 감지한다.

## 24pg.

HDBSCAN
- 가속화된 hierachical density based clustering
- OPTICS와 유사한 cluster를 감지한다
- OPTICS보다 더 빠르지만 memory를 많이 필요로한다

## 25pg.

DENCLUE
- density based clustering
- cluster는 KDE(kernel density estimation)로 model된다.

data 공간의 전체 밀도는 모든 data points의 influence 함수의 합으로 계산될 수 있다.  
cluster는 density attractors를 식별하여 수학적으로 결정. 이는 전체 density func의 local maxima  
data poins는 hill climbing을 통해 density attractor에 할당된다. 즉 동일한 지역 최대값으로 이동하는 points는 동일한 cluster로 배정된다  
고밀도(threshold) path를 통해 연결된 density attractor를 병합한다.  

## 28pg.

Grid-based clustering
- multi-resolution grid data structure 사용
- Sting - 통계 정보 grid 접근
- Clique - grid 기반 및 subspace clustering

## 29 ~ 30pg.

STING
- Statistical information grid approach
- spatial area가 직사각형 셀로 나뉜다.
- 다양한 resolution(해상도) level에 해당하는 여러 level의 cell이 있다.

높은 level의 각 cell은 다음 낮은 level에서 여러 작은 cell로 분할된다.  

각 cell의 통계 정보가 미리 계산되고 저장되며, queries에 답하는데 사용된다.
- count, mean, std, min, max
- 분포 유형 - normal, uniform 등등
- 높은 level cell의 매개변수는 낮은 level의 매개변수에서 쉽게 계산된다.

spatial data queries에 대한 top-down 방식
- 더 이상 고려하지 않을 무관한 cell 제거
- 현재 layer 조사하고 다음 낮은 level 진행
- process의 바닥 layer에 도달할 때까지 반복

장점 - query independent, 병렬화 쉽다, incremental(점차적) update  
단점 - 모든 cluster 경계는 수평 혹은 수직, 대각선 경계는 감지되지 않는다.  

## 31 ~ 32pg.

CLIQUE (Clustering In QUEst)
- 고차원 데이터 공간에서 원래 공간보다 더 나은 clustering을 허용하는 subspace를 자동 식별

CLIQUE 는 density-based, grid-based로 간주될 수 있다.
- 각 차원을 동일한 수의 동일한 길이로 분할
- unit는 subspace에 겹치지 않는 직사각형 영역
- unit은 해당 입력 매개변수를 초과하는 경우 밀도가 높다
- cluster는 subspace 내에서 연결된 dense unit의 최대 집합

Apriori 원칙을 사용하여 클러스터를 포함하는 부분 공간을 식별
- 각 차원을 분할하고, 각 차원에서 dense units을 찾는다
- 각각이 dense units를 가지는 두 차원 merge
- 두 차원 merge할 때, each unit의 size가 감소
- unit이 dense되지 않으면, subspace를 확장할 필요 없다.

cluster 식별
- 관심 있는 모든 subspace에서 dense units을 결정
- 관심 있는 모든 subspace에서 connected dense units을 결정

Properties
- cluster가 존재하는 가장 높은 차원을 차즌ㄴ다.
- 어떤 canonical data 분포도 가정하지 않고 임의의 형태로 cluster를 찾는다
- 입력 size에 따라 linearly하게 확장
- 이론적으로 지수적이지만, 실제로는 일정 정도의 차원 수에 대해 확장 가능

