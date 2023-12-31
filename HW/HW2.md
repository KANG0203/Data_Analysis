# SQLite

## db파일 연결 및 table 생성

>data = sqlite3.connect("파일")

db파일을 연결하는 함수이다. 만약 마지막에 data.commit()를 안하려면 파일 명 뒤에 isolation_level = Nobe 을 추가한다.    
>cur = data.cursor()  

data를 control할 cursor을 연결하는 함수이다.  

>cur.execute("create table if not exist 이름(column 타입, ...)")

table을 만드는 함수이다.  
"if not exist"는 해당 table이 없다면 생성하는 조건이다.  
괄호 안에는 column에 들어갈 이름과 타입을 적는데, string이면 text, int면 integer 라고 적는다.  

> input_list = [(),(),..]  
cur.excutemany("insert into 이름(column, ...) values(?,?,...), input list)

table에 들어갈 내용을 list로 만든다.  
column 순서대로 적고, string인 경우 ''를 씌운다.
이후 입력값이 많으므로 cur.excutemany를 통해 input list를 table에 추가한다. 

>data.commit()  
cur.close()  
data.close()  

마무리 할 때 추가하자. 

<details>
<summary> problem 1.a </summary>
<div markdown="1">

```python
def create() -> None:
    '''
        create() connects a database named |titanic.db| and creates a table |Company| in it.

        Columns and data types of table |Company| are as follow:
            |Employee|   - string
            |Department| - string
            |Salary|     - int
            |Gender|     - string
        
        The order of data insertion does not matter.
    '''
    # BEGIN_YOUR_CODE
    
    data = sqlite3.connect("titanic.db")
    cur = data.cursor()
    cur.execute("create table if not exists Company(Employee text, Department text, Salary integer, Gender text)")
    input_list = [('John', 'sales', 5000, 'M'), 
            ('Allen', 'accounting', 6000, 'M'), 
            ('Martin', 'research', 3500, 'M'), 
            ('Mary', 'sales', 5500, 'F'), 
            ('Smith', 'research', 4500, 'M')]
    cur.executemany("insert into Company (Employee, Department, Salary, Gender) values(?,?,?,?)", input_list)
    data.commit()
    cur.close()
    data.close()
    
    # END_YOUR_CODE
    
create()
```

</div>
</details>  

## table fetch

>cur.execute("select * from 이름")

table 모든 내용 선택

>cur.fetchall()

모든 내용 fetch

>cur.execute("select * from 이름 where ~ order by ~")

where문은 조건을 추가한다.  
만약 조건이 여러개라면 and를 추가한다.  
order by는 뒤에 column 이름을 쓴다. 오름차순이면 이름만, 내림차순이면 desc  

<details>
<summary> problem 1.c </summary>
<div markdown="1">

```python
def select2() -> List[Tuple[int, str, int, int]]:
    '''
        select2() fetches all data satisfying certain condition from table |Titatic| in database |titanic.db|
            and returns them as a list of tuples.

        Columns and data types of table |Titanic| are as follow:
            |Pclass|   - int
            |Name|     - string
            |Survived| - int
            |Age|      - int
        
        The returned list should be formatted as follow:
            [ Tuple_1, ..., Tuple_N ]
            where N is # of fetched data and
            Tuple_n = ( |Pclass|, |Name|, |Survived|, |Age| ), |Survived| == 1, |Age| < 65
            for 1 <= n <= N.

        The tuples should be arranged in ascending order of |Age|.
        The order of tuples with the same |Age| does not matter.
    '''
    # BEGIN_YOUR_CODE
    
    data = sqlite3.connect("titanic.db")
    cur = data.cursor()
    cur.execute("select * from Titanic where Survived == 1 and Age < 65 order by Age")
    return (cur.fetchall())

    # END_YOUR_CODE

select2()
```

</div>
</details> 

>cur.execute("select ... form 이름 group by ...")

group by를 하려면 마지막에 원하는 column을 적어준다.  
원하는 column만 select하고 싶으면 select 다음에 원하는 column을 적는다.  
평균 값을 가져오고 싶으면 avg(column)을 이용한다.  

>cur.execute("select * from 이름 (left/right/full) outer join 이름 on 조건")

join하는 방법이다.  
inner join을 하려면 그냥 join만 적어줘도 된다.  
outer join을 하려면 원하는 방향을 적고 outer join을 적는다.  
on 뒤에는 원하는 조건을 적는다.  

<details>
<summary> problem 1.d,e ex </summary>
<div markdown="1">

```python

cur.execute("select Pclass, avg(Age) from Titanic group by Pclass")
cur.execute("select * from Company left outer join Titanic on Company.Employee == Titanic.Name")

```

</div>
</details> 

## SQLite and Pandas

>pd.read_sql("select * from 이름", data, index_col = None)

table(database)를 dataframe으로 바꿔주는 함수이다.  

>df.to_sql('이름', data)

dataframe을 database로 바꿔주는 함수이다.

<details>
<summary> problem 2 </summary>
<div markdown="1">

```python

#db to df
data = sqlite3.connect("titanic.db")
df = pd.read_sql("select * from Titanic", data, index_col = None)
df.to_csv("titanic.csv")

#df to db
df = pd.read_csv("titanic2.csv", index_col = 0)  
data = sqlite3.connect("titanic.db")
df.to_sql('Titanic2', data)

```

</div>
</details> 
