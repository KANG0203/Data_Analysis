## SQL exercise

1. select country, branch, num(accounts) from Bank group by country, branch
2. select country, sum(balance) from Bank group by country order by sum(balance) DESC

이 부분은 시험 전에 은이랑 맞춰보자.  

## Interpreting complicated SQL
딱 보아하니 시험에 안나올 것 같으니 pass  

## User-defined function  
1. scalar fun - select, where
2. Aggregate fun - select, Group by
3. Table fun - select ~ from ~

## Same logical expression, different physical algorithm
select * from order o, item i where o.order = i.order  

option 1 : Nested loop join (O(n^2))
option 2 : Hash join  

 
