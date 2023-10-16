## Algebraic optimization
Algebraic Laws: 
1. Additive indentity x + 0 = x
2. Divisive identity x/1 = x
3. Distributive law - (n*x + n*y) = n*(x + y)
4. Commutative law - x*y = y*x

Two operations instead of five, no division operator

## Equivalent logical expressions, different cost
right associative, left associative, cross product - 아마 이 page에서는 cross product의 cost가 젤 적은 것으로 추정된다.  

## Relational algebra operators
RA - union, intersection, difference, selection, projection, join  
Extended RA - duplicate elimination(t), Grouping and aggregation(g), sorting(t)

## Set vs. Bag (vs. List)
Sets : 순서가 없으며, 중복 허용 x  
Bags : 순서가 없으며, 중복 허용 o  
list : 순서가 있으며, 중복 허용 o  

paper : set semantics, standard relational algebra is usually enough.  
implementation : bag semantics, extened relational algebra is need.  

## RA
1. Selection  
Return all tuples that saticfy a condition c.  
EX> sigma_salary > 40000_(Employee) -> select * from employee where salary > 40000

2. Union
R1 U R2
중복 허용하면서 합침 (all 붙이면 중복 허용임)  
EX> select * from R1 union all select * from R2

4. Set difference  
R1 - R2
R1에 있는 row가 R2에도 있으면 R1에서 제거
EX> select * from R1 except select * from R2

5. Intersection
derived operator using minus : R1 교집합 R2 = R1 - (R1 - R2)
derived using join

6. Projection
선택한 columns 말고 eliminates하는 것이다.
pi_A1,...,An_(R)
EX> select SSN, Name frkom employee

7. Cartesian product
R1 X R2  
Combine exch tuple in R1 and each tuple in R2

8. Equi-join
R1_|><|_A=B_R2 는 sigma_A=B_(R1XR2) 와 같다.
A join that involves a predicate theta
select * from R1, R2 where R1.A = R2.B

10. Theta-join
R1_|><|_theta_R2 = sigma_theta_(R1XR2)  
A join that involves a predicate theta, theta can be any condition.
Equi-join은 theta가 equality condition인 special case.

11. Natural join
R1 |><| R2  
곂치는 columns 있으면 값도 같아야지 합쳐진다.
이걸로 위에 나온 Intersection을 join으로 표현할 수 있다.

12. Outer join
NULL을 이용해서 없는 값을 채운다.
1. left outer join
2. right outer join
3. Full outer join

13. Aggregation : Group by
func : sum, count, average, maximum, minimum
EX> find the maximum balance of each branch
1. branch_G_max(Balance)_(Bank)
2. select branch, max(Balance) from Bank group by branch

조건을 추가할 때 where이 아니라 having을 쓴다.  
Ex> find balance sum of each branch whose sum is larger than 10000  
1. sigma_sum(balance)>10000_(branch_G_sum(balance)_(Bank))
2. select branch, sum(balance) from bank group by branch having sum(balance) > 10000

우선순위 정렬할 때 order by를 쓴다.  
EX> output balance sum of Korea branches whose sum is larger than 10000 in ascending order  
1. sigma_sum(balance)>100000_(branch_G_sum(balance)_(sigma_country=korea_(Bank)))
2. select branch, sum(balance) from Bank where branch = korea group by branch having sum(balance) > 10000 order by sum(balance) ASC
내림차순은 DESC으로 쓴다.

