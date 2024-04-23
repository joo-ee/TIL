### join의 on절과 where절 😶‍🌫️

분명 간단한 내용인데 혼자 이상한 데에 꽂혀서 제대로 이해를 못하고 있는 것 같아서 정리 ...

SQL의 JOIN에서 `ON`과 `WHERE`절의 차이점은 JOIN하는 범위에 있다.

1. `ON` 절에 조건을 넣는 경우:

   - ON 절에 조건을 넣으면 JOIN 시에 두 테이블 간의 관계를 정의하게 된다. 즉, 조인될 레코드를 결정하는 것.
   - ON 절에서 조건을 지정하면 해당 조건이 JOIN에 참여하는 행만을 선택하므로, 조인된 결과는 해당 조건을 만족하는 행만 포함하게 된다.

2. `WHERE` 절에 조건을 넣는 경우:
   - WHERE 절에 조건을 넣으면 JOIN 후에 결과에 대한 추가적인 필터링을 수행한다.
   - WHERE 절에 조건을 넣으면 JOIN 조건과는 관계 없이, 조인된 결과 중에서 해당 조건을 만족하는 행만을 선택한다.

😵‍💫

다음과 같이 테이블 A와 테이블 B가 있다고 했을 때,

테이블 A :

```lua
| no | name  |
|----|-------|
| 1  | Alice |
| 2  | Bob   |
| 3  | Carol |

```

테이블 B :

```lua
| no | name  |
|----|-------|
| 1  | NULL |
| 2  | Bob   |
| 3  | Carol |

```

동일하게 `B.name is not NULL` 조건을 걸었을 때 결과가 어떻게 나오는지 보자.

1. `ON` 절에 조건을 넣는 경우

```sql
SELECT *
FROM A
LEFT JOIN B ON A.no = B.no AND B.name IS NOT NULL;
```

결과:

```lua
| A.no | A.name | B.no | B.name |
|------|--------|------|--------|
| 1 | Alice | NULL | NULL |
| 2 | Bob | 2 | Bob |
| 3 | Carol | 3 | Dave |
```

2. `WHERE` 절에 조건을 넣는 경우

```sql
SELECT *
FROM A
LEFT JOIN B ON A.no = B.no
WHERE B.name IS NOT NULL;
```

결과:

```lua
| A.no | A.name | B.no | B.name |
|------|--------|------|--------|
| 2    | Bob    | 2    | Bob    |
| 3    | Carol  | 3    | Dave   |
```

~~헉 역시 정리하니까 이해가 된다 !~~

1)의 경우는 (A 테이블)과 (B 테이블 중 `B.name IS NOT NULL`인 경우)를 JOIN 한 결과가 나오지만 2)의 경우는 A와 B테이블의 JOIN을 수행한 후에 `B.name IS NOT NULL`인 데이터들을 추출하게 되는 것!

그래서 1은 B.name이 NULL인 데이터도 존재할 수 있게 된다 ... !
