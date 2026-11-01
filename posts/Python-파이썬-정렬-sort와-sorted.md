---
title: "[Python] 파이썬 정렬 - sort와 sorted"
date: 2026-09-29T12:32:05.787Z
tags: ["python"]
velog_slug: Python-파이썬-정렬-sort와-sorted
---
# 파이썬 정렬 - sort와 sorted

**한 줄 기준: 원본을 지켜야 하면 `sorted()`, 원본을 바꿔도 되면 `.sort()`.**


## 비유로 이해하기
- **`.sort()`** = 책장의 책을 **직접 꺼내 다시 꽂는 것**. 책장(원본)이 바뀌고, 따로 남는 결과물은 없음
- **`sorted()`** = 책장은 그대로 두고, **정렬된 목록을 종이에 새로 적어 주는 것**. 원본은 그대로이고 새 목록이 생김

## 비교
| | `리스트.sort()` | `sorted(데이터)` |
|---|---|---|
| 정체 | 리스트의 **메서드** | 파이썬 **내장 함수** |
| 원본 | **바뀜** (in-place) | **그대로** |
| 돌려주는 값 | `None` (아무것도 안 줌) | 정렬된 **새 리스트** |
| 쓸 수 있는 대상 | 리스트만 | 튜플, 문자열, 딕셔너리, set 등 반복 가능한 것 전부 |
| 메모리 | 복사 안 함 → 조금 더 효율적 | 복사본을 하나 더 만듦 |

```python
a = [3, 1, 2]

b = sorted(a)
print(a)   # [3, 1, 2]  ← 원본 그대로
print(b)   # [1, 2, 3]  ← 새 리스트

a.sort()
print(a)   # [1, 2, 3]  ← 원본이 바뀜
```

## 공통 옵션: key, reverse
둘 다 사용법이 같음.
```python
words = ['banana', 'kiwi', 'apple']

sorted(words)                          # ['apple', 'banana', 'kiwi']  가나다(알파벳)순
sorted(words, reverse=True)            # ['kiwi', 'banana', 'apple']  역순
sorted(words, key=len)                 # ['kiwi', 'apple', 'banana']  길이순
```
- `reverse=True`: 내림차순
- `key=함수`: "무엇을 기준으로 줄 세울지" 지정. 각 원소에 함수를 적용한 결과로 비교함

## 자주 하는 실수
- **`.sort()` 결과를 변수에 담기** — `x = a.sort()` 하면 `x`는 `None`. `.sort()`는 원본만 바꾸고 결과를 돌려주지 않음
- **튜플·문자열에 `.sort()` 쓰기** — 이 둘은 바꿀 수 없는(immutable) 자료형이라 `.sort()` 메서드가 없음 → `sorted()`를 써야 함
- **`sorted()` 결과의 자료형** — 무엇을 넣든 결과는 **항상 리스트**. `sorted("cba")` → `['a', 'b', 'c']` (문자열 아님)

## 이론 ↔ 실무 연결
이 차이는 정렬에만 해당하지 않음. **"원본을 바꾸느냐, 새 결과를 돌려주느냐"**는 파이썬과 pandas 전반에 계속 나오는 패턴임.

| 원본을 바꾸는 쪽 | 새 결과를 돌려주는 쪽 |
|---|---|
| `list.sort()` | `sorted()` |
| `list.reverse()` | `reversed()` |
| `df.sort_values(..., inplace=True)` | `df.sort_values(...)` |

```python
df_sorted = df.sort_values('price')          # sorted()처럼 새 DataFrame 반환
df.sort_values('price', inplace=True)        # .sort()처럼 원본 수정, None 반환
```

- 데이터 분석에서는 **새 결과를 돌려주는 방식**을 기본으로 씀. 원본 데이터를 보존해야 전처리 단계를 되돌리거나 비교하기 쉬움
- pandas에서도 요즘은 `inplace=True`보다 `df = df.sort_values(...)`처럼 **결과를 다시 변수에 담는 방식**을 권장함
- Jupyter에서 원본을 바꾸는 코드가 든 셀을 여러 번 실행하면 데이터가 의도와 다르게 꼬이기 쉬움. 새 결과를 돌려주는 방식이면 이런 문제가 줄어듦




