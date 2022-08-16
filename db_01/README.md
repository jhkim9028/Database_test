# 사전 설정

## 실행

```bash
$ sqlite3 healthcare.sqlite3 
```

## Column 출력 설정

```sql
sqlite3> .headers on 
sqlite3> .mode column
```

## table 및 스키마 조회

```sql
sqlite3> .tables
healthcare

sqlite3> .schema healthcare
CREATE TABLE healthcare (
id PRIMARY KEY,        
sido INTEGER NOT NULL, 
gender INTEGER NOT NULL,
age INTEGER NOT NULL,  
height INTEGER NOT NULL,
weight INTEGER NOT NULL,
waist REAL NOT NULL,   
va_left REAL NOT NULL, 
va_right REAL NOT NULL,

blood_pressure INTEGER 
NOT NULL,
smoking INTEGER NOT NULL,
is_drinking BOOLEAN NOT NULL
);
```

# 문제

### 1. 추가되어 있는 모든 데이터의 수를 출력하시오.

```sql
SELECT COUNT(*) FROM healthcare;
```

```
COUNT(*)
--------
1000000
```

### 2. 나이 그룹이 10(age)미만인 사람의 수를 출력하시오.

```sql
SELECT COUNT(*) FROM healthcare WHERE age < 10;
```

```
count(*)
--------
156277
```

### 3. 성별이 1인 사람의 수를 출력하시오.

```sql
SELECT COUNT(*) FROM healthcare WHERE gender = 1;
```

```
count(*)
--------
510689
```

### 4. 흡연 수치(smoking)가 3이면서 음주(is_drinking)가 1인 사람의 수를 출력하시오.

```sql
SELECT COUNT(*) FROM healthcare WHERE smoking = 3 and is_drinking = 1;
```

```
count(*)
--------
150361
```

### 5. 양쪽 시력이(va_left, va_right) 모두 2.0이상인 사람의 수를 출력하시오.

```sql
SELECT COUNT(*) FROM healthcare WHERE va_left >= 2.0 and va_right >= 2.0;
```

```
count(*)
--------
2614
```

### 6. 시도(sido)를 모두 중복 없이 출력하시오.

```sql
SELECT DISTINCTsido FROM healthcare;
```

```
36
27
11
31
41
44
48
30
42
43
46
28
26
47
45
29
49
```

### 자유롭게 조합해서 원하는 데이터를 출력해보세요.

> 예) 허리 둘레가 x이상이면서 몸무게가 y이하인 사람

몸무게가 35 미만이면서 혈압이 90미만인 사람의 모든 정보

```sql
SELECT COUNT(*) FROM healthcare WHERE weight < 35 and blood_pressure < 90;
```

```sql
id      sido  gender  age  height  weight  waist  va_left  va_right  blood_pressure  smoking  is_drinking
------  ----  ------  ---  ------  ------  -----  -------  --------  --------------  -------  -----------
42961   44    2       17   145     30      79.0   0.1      0.1       81              1        0
120854  44    2       11   150     30      60.0   1.0      1.0       89              1        1
177416  45    2       13   145     30      56.0   0.8      0.5       85              1        0
194983  41    2       13   155     30      58.0   0.5      1.0       84              1        0
600511  27    2       11   150     30      53.0   1.0      1.2       89              1        0
614008  44    2       18   130     30      70.0   0.1      0.1       89              1        0
632570  30    2       11   155     30      52.0   0.3      0.4       87              1        0
792239  28    2       9    135     30      58.3   0.8      1.2       88              1        0
```