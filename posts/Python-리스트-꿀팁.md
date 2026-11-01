---
title: "[Python] 리스트 꿀팁"
date: 2026-09-29T13:04:08.987Z
tags: ["python"]
velog_slug: Python-리스트-꿀팁
---

# 파이썬 리스트 활용

**한 줄 요약: 리스트에서 자주 하는 일(값 찾기, 정렬, 뒤집기, 삭제)은 파이썬에 이미 기능이 들어 있다. 직접 만들지 말고 가져다 쓰면 된다.**


## 1. 값이 있는지 확인하기: `in` / `not in`
직접 함수를 만들면 이렇게 됨. 리스트를 앞에서부터 하나씩 비교하다가 찾으면 `True`, 끝까지 없으면 `False`를 돌려줌.
```python
# value가 some_list의 요소인지 확인
def in_list(some_list, value):
    i = 0
    while i < len(some_list):
        # some_list에서 value를 찾으면 True를 리턴
        if some_list[i] == value:
            return True
        i = i + 1

    # 만약 some_list에서 value를 발견하지 못했으면 False를 리턴
    return False
    
    # 테스트
	primes = [2, 3, 5, 7, 11, 13, 17, 19, 23]
	print(in_list(primes, 7))  # -> True
	print(in_list(primes, 12)) # -> False


```
너무 자주 쓰는 기능이라 파이썬에는 `in` 키워드로 이미 들어 있음.
```python
primes = [2, 3, 5, 7, 11, 13, 17, 19, 23]

7 in primes        # True
12 in primes       # False
7 not in primes    # False  ← "없는지" 확인
12 not in primes   # True
```
- 결과는 항상 `True` 또는 `False`여서 `if` 조건문에 바로 넣어 쓸 수 있음
- 내부 동작은 위의 `in_list`와 같음. **앞에서부터 하나씩 확인**하므로 리스트가 길수록 느려짐

## 2. 리스트 안의 리스트 (Nested List)
리스트의 원소로 또 리스트를 넣을 수 있음. **표(행과 열)**라고 생각하면 쉬움.
```python
# 학생 3명 × 시험 3번
grades = [[62, 75, 77],   # 학생 0
          [78, 81, 86],   # 학생 1
          [85, 91, 89]]   # 학생 2

grades[0]       # [62, 75, 77]  첫 번째 학생의 성적 전체 (행 하나)
grades[2][1]    # 91            세 번째 학생의 두 번째 시험
                #  ↑행   ↑열

# 첫 번째 시험의 평균 (열 하나를 세로로 모으기)
(grades[0][0] + grades[1][0] + grades[2][0]) / 3   # 75.0
```
- `[행][열]` 순서로 인덱싱함. 대괄호 하나를 쓸 때마다 한 단계 안으로 들어감
- **행 하나는 꺼내기 쉽지만 열 하나(시험별 평균)는 일일이 모아야 해서 불편함** → 이 불편함 때문에 pandas를 씀 (아래 실무 연결 참고)

## 3. 리스트 메서드 정리
| 메서드 | 하는 일 | 원본 변경 | 주의할 점 |
|---|---|---|---|
| `lst.sort()` | 오름차순 정렬 | O | 결과를 돌려주지 않음(`None`). → [[파이썬 정렬 - sort와 sorted]] |
| `lst.reverse()` | 순서를 **거꾸로** 뒤집음 | O | 정렬이 아님. 지금 순서를 그대로 뒤집기만 함 |
| `lst.index(x)` | `x`가 **처음** 나오는 위치(인덱스) | X | `x`가 없으면 **에러(ValueError)** |
| `lst.remove(x)` | `x`를 **처음 하나만** 삭제 | O | 같은 값이 여러 개면 첫 번째만 지워짐. 없으면 **에러** |

```python
numbers = [5, 3, 7, 1]
numbers.sort()       # [1, 3, 5, 7]

numbers = [5, 3, 7, 1]
numbers.reverse()    # [1, 7, 3, 5]  ← 내림차순 [7, 5, 3, 1]이 아님!

members = ["영훈", "윤수", "태호", "혜린"]
members.index("윤수")   # 1  (0부터 셈)

fruits = ["딸기", "당근", "파인애플", "수박"]
fruits.remove("파인애플")   # ['딸기', '당근', '수박']
```

## 자주 하는 실수
- **`reverse()`를 내림차순 정렬로 착각** — 내림차순은 `lst.sort(reverse=True)`. `reverse()`는 순서만 뒤집음
- **없는 값에 `index()`·`remove()` 쓰기** — 에러가 나서 프로그램이 멈춤. `in`으로 먼저 확인하는 습관을 들이면 안전함
  ```python
  if "민지" in members:
      members.remove("민지")
  ```
- **메서드 결과를 변수에 담기** — `sort()`, `reverse()`, `remove()`는 원본만 바꾸고 `None`을 돌려줌. `x = fruits.remove("수박")` → `x`는 `None`

## 이론 ↔ 실무 연결
| 오늘 배운 것 | 실무에서 만나는 모습 |
|---|---|
| `x in 리스트` | SQL의 `WHERE 컬럼 IN (...)`과 같은 발상 → [[SQL WHERE 조건 - IN과 LIKE]]. pandas에서는 `df[df['지역'].isin(['서울', '부산'])]` |
| `in`이 앞에서부터 하나씩 찾는다는 점 | 값이 많고 자주 찾아야 하면 리스트 대신 `set`(집합)을 씀. `set`은 크기와 상관없이 거의 바로 찾음 |
| Nested list (`grades[행][열]`) | pandas DataFrame, numpy 2차원 배열의 기초. `grades` 예시의 "시험별 평균"은 DataFrame에서 `df.mean()` 한 줄로 끝남 |
| 원본을 바꾸는 메서드(`sort`, `reverse`, `remove`) | pandas `inplace=True`와 같은 개념. 분석에서는 원본을 보존하는 쪽이 기본 → [[파이썬 정렬 - sort와 sorted]] |

→ 이 파트의 핵심은 **"자주 하는 일은 이미 만들어져 있다"**는 것. `in_list`를 직접 짜보는 건 원리 이해용이고, 실무에서는 내장 기능을 쓰는 게 더 빠르고 실수도 적음.

