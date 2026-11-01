---
title: "[SQL(BigQuery)] SQL `WHERE`와 `HAVING` 차이"
date: 2026-09-23T12:19:57.248Z
tags: ["sql"]
velog_slug: SQLBigQuery-SQL-WHERE와-HAVING-차이
---
# SQL `WHERE`와 `HAVING` 차이

SQL을 공부하다 보면 `WHERE`와 `HAVING`이 헷갈릴 때가 많다.

둘 다 **조건을 걸어 데이터를 필터링**하는 역할을 하지만,
가장 큰 차이는 **언제 조건을 적용하느냐**이다.

> **WHERE = 집계하기 전 조건**
> **HAVING = 집계한 후 조건**

---

## 1. WHERE란?

`WHERE`는 **테이블의 원본 데이터에서 조건에 맞는 행(row)을 먼저 골라내는 것**이다.

예를 들어 학생 테이블이 있다고 하자.

| 학생 | 학과 | 점수 |
| -- | -- | -: |
| 철수 | 컴공 | 90 |
| 영희 | 컴공 | 80 |
| 민수 | 경영 | 70 |
| 지수 | 경영 | 95 |

컴퓨터공학과 학생만 조회하고 싶다면:

```sql
SELECT *
FROM students
WHERE department = '컴공';
```

### 실행 결과

| 학생 | 학과 | 점수 |
| -- | -- | -: |
| 철수 | 컴공 | 90 |
| 영희 | 컴공 | 80 |

즉, `WHERE`는 **각각의 행을 하나씩 확인하면서 조건에 맞는 데이터만 남긴다.**

```text
전체 학생
   ↓
WHERE department = '컴공'
   ↓
컴공 학생만 남음
```

---

# 2. HAVING이란?

`HAVING`은 **`GROUP BY`를 사용해서 데이터를 그룹화하고 집계한 결과에 조건을 걸 때** 사용한다.

예를 들어 학과별 평균 점수를 구해보자.

```sql
SELECT
    department,
    AVG(score) AS avg_score
FROM students
GROUP BY department;
```

### 결과

| 학과 | avg_score |
| -- | --------: |
| 컴공 |        85 |
| 경영 |      82.5 |

여기서 **평균 점수가 83점 이상인 학과만** 보고 싶다면 `HAVING`을 사용한다.

```sql
SELECT
    department,
    AVG(score) AS avg_score
FROM students
GROUP BY department
HAVING AVG(score) >= 83;
```

### 결과

| 학과 | avg_score |
| -- | --------: |
| 컴공 |        85 |

왜 `WHERE`가 아니라 `HAVING`을 사용할까?

`AVG(score)`는 원래 테이블에 존재하는 값이 아니라,
`GROUP BY`를 통해 **계산된 값**이기 때문이다.

---

# 3. WHERE와 HAVING의 핵심 차이

| 구분                    | WHERE         | HAVING               |
| --------------------- | ------------- | -------------------- |
| 적용 시점                 | 집계 전          | 집계 후                 |
| 대상                    | 개별 행(row)     | 그룹(group)            |
| 주로 사용                 | 일반적인 조건       | 집계 결과 조건             |
| `COUNT`, `SUM`, `AVG` | 일반적으로 직접 사용 X | 사용 가능                |
| `GROUP BY`와 관계        | 없어도 사용 가능     | 보통 `GROUP BY`와 함께 사용 |

쉽게 생각하면:

> **WHERE → "데이터를 먼저 골라!"**
> **GROUP BY → "비슷한 것끼리 묶어!"**
> **HAVING → "묶은 결과 중에서 다시 골라!"**

---

# 4. WHERE와 HAVING을 같이 사용하는 경우

실무에서는 둘을 같이 사용하는 경우도 많다.

```sql
SELECT
    department,
    COUNT(*) AS student_count
FROM students
WHERE score >= 80
GROUP BY department
HAVING COUNT(*) >= 2;
```

이 SQL을 순서대로 해석해보자.

### ① FROM

먼저 `students` 테이블에서 데이터를 가져온다.

```sql
FROM students
```

### ② WHERE

80점 이상인 학생만 남긴다.

```sql
WHERE score >= 80
```

### ③ GROUP BY

남은 학생들을 학과별로 묶는다.

```sql
GROUP BY department
```

### ④ COUNT

각 학과의 학생 수를 계산한다.

```sql
COUNT(*)
```

### ⑤ HAVING

학생 수가 2명 이상인 학과만 남긴다.

```sql
HAVING COUNT(*) >= 2
```

### 전체 흐름

```text
전체 학생
   ↓
WHERE score >= 80
   ↓
80점 이상 학생
   ↓
GROUP BY department
   ↓
학과별 그룹 생성
   ↓
COUNT(*)
   ↓
학과별 학생 수 계산
   ↓
HAVING COUNT(*) >= 2
   ↓
학생 수가 2명 이상인 학과
```

---

# 5. 집계 함수와 HAVING

`HAVING`을 이해하려면 **집계 함수(Aggregate Function)**도 알아야 한다.

집계 함수는 여러 행의 데이터를 계산해서 **하나의 결과로 만들어주는 함수**이다.

대표적인 집계 함수:

```sql
COUNT()  -- 개수
SUM()    -- 합계
AVG()    -- 평균
MAX()    -- 최대값
MIN()    -- 최소값
```

예를 들어:

```sql
SELECT
    department,
    COUNT(*) AS count
FROM students
GROUP BY department;
```

학과별 학생 수를 계산할 수 있다.

그리고 그 결과에 조건을 걸고 싶다면:

```sql
HAVING COUNT(*) >= 10;
```

즉,

> **학생 수가 10명 이상인 학과만 보여줘**

라는 뜻이다.

---

# 6. 가장 쉽게 기억하는 방법

문제를 읽을 때 다음과 같이 생각하면 된다.

### "80점 이상인 학생을 찾아라"

```sql
WHERE score >= 80
```

개별 학생의 점수를 기준으로 판단하기 때문에 `WHERE`.

---

### "평균 점수가 80점 이상인 학과를 찾아라"

```sql
HAVING AVG(score) >= 80
```

학과별로 평균을 계산한 뒤 판단하기 때문에 `HAVING`.

---

### "학생 수가 10명 이상인 학과를 찾아라"

```sql
HAVING COUNT(*) >= 10
```

학과별 학생 수를 계산한 뒤 판단하기 때문에 `HAVING`.

---

# 7. 한 줄 요약

```text
WHERE
→ 원본 데이터에 조건
→ 집계하기 전에 필터링

HAVING
→ 집계 결과에 조건
→ 집계한 후 필터링
```

### ⭐ 핵심 암기

> **WHERE = 행을 필터링**
> **HAVING = 그룹을 필터링**

특히 `COUNT()`, `SUM()`, `AVG()` 같은 **집계 함수의 결과에 조건을 걸어야 한다면 HAVING**을 먼저 떠올리자.
