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
