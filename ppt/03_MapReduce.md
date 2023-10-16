## read trimming
data를 read하기 전에 k개로 나누어서 함수 f를 모든 item에 적용하여 read 한다. -> O(n/k)  
map 함수를 통해 나누어서 계산하고, shuffle 한 다음 reduce한다.  

함수  

map(string in_key, string in_value):  
  For each word w in in_value:  
    Emit(w,1);  

reduce(string intermediate_key, iterator intermediate_values):  
  int result = 0;  
  for each v in intermediate_values:  
    result += v;  
  Emit(intermediate_key, result);  

입력이 이상하게 되니깐 교제 봐라.  
map 함수에서는 1개씩 계속 추출한다.  

여기 부분은 ppt를 보자 내용이 너무 방대함.  

## cluster computing
Large number of commondity servers, connected by commdity network.  
Rack : holds a small number of servers  
Data center : holds many racks  
Massive parallelism : 100s, 1000s, or 10000s servers  
Failure : if mean-time-between-failure is year, then 10000 servers have on failure per hour  

## Distriubted file system (DFS)  
For very large files : TBs, PBs  
각 file은 일반적으로 64MB로 나눠진다.(chunk)  
각 chunk는 fault tolerance 때문에 다른 rack에 3번 이상 복제된다.  

## Large-scale data processing  
MapReduce는 lightweight framework로 다음을 제공한다.  
1. automatic parallelization and distribution
2. Fault-tolerance (장애 발생해도 정상적 혹은 부분적으로 기능을 수행할 수 있는 시스템)
3. status and monitoring
