---
title: "[Python] 리스트 내포(List Comprehension) 쉽게 이해하기"
date: 2026-10-02T07:17:10.265Z
tags: ["python"]
velog_slug: Python-리스트-내포List-Comprehension-쉽게-이해하기
---
# 리스트 내포(List Comprehension) 쉽게 이해하기

## 1. 예제 코드

```python
base_deposits = [1000, 2000, 3000, 4000]

tripled = [amount * 3 for amount in base_deposits if (amount // 1000) % 2 == 0]

print('리스트 내포:', tripled)
```

실행 결과:

```text
리스트 내포: [6000, 12000]
```

---

## 2. 먼저 `base_deposits` 이해하기

```python
base_deposits = [1000, 2000, 3000, 4000]
```

예금액 4개가 들어 있는 리스트이다.

```text
1000
2000
3000
4000
```

---

## 3. 리스트 내포(List Comprehension)란?

리스트 내포는 **반복문과 조건문을 한 줄로 작성해서 새로운 리스트를 만드는 방법**이다.

기본 형태는 다음과 같다.

```python
[변환할 값 for 변수 in 리스트 if 조건]
```

이번 예제에서는:

```python
[amount * 3 for amount in base_deposits if (amount // 1000) % 2 == 0]
```

각 부분은 다음과 같다.

| 부분 | 의미 |
|---|---|
| `amount * 3` | 최종적으로 리스트에 넣을 값 |
| `for amount in base_deposits` | 리스트에서 값을 하나씩 꺼냄 |
| `if (amount // 1000) % 2 == 0` | 조건에 맞는 값만 선택 |

쉽게 말하면:

> `base_deposits`에서 `amount`를 하나씩 꺼낸다 → 조건을 확인한다 → 조건에 맞으면 `amount * 3`을 해서 새 리스트에 넣는다.

---

## 4. 리스트 내포를 일반적인 `for`문으로 바꾸기

다음 코드:

```python
tripled = [amount * 3 for amount in base_deposits if (amount // 1000) % 2 == 0]
```

은 일반적인 `for`문으로 풀면 다음과 같다.

```python
tripled = []

for amount in base_deposits:
    if (amount // 1000) % 2 == 0:
        tripled.append(amount * 3)
```

즉, 리스트 내포는 긴 코드를 짧게 표현한 것이라고 생각하면 쉽다.

---

## 5. `//`는 무엇인가?

`//`는 **나눗셈의 몫만 구하는 연산자**이다.

예:

```python
1000 // 1000
# 1

2000 // 1000
# 2

3000 // 1000
# 3

4000 // 1000
# 4
```

따라서:

| `amount` | `amount // 1000` |
|---:|---:|
| 1000 | 1 |
| 2000 | 2 |
| 3000 | 3 |
| 4000 | 4 |

---

## 6. `%`는 무엇인가?

`%`는 **나머지를 구하는 연산자**이다.

예:

```python
1 % 2
# 1

2 % 2
# 0

3 % 2
# 1

4 % 2
# 0
```

특히 `% 2 == 0`은 **짝수인지 확인할 때 자주 사용하는 방법**이다.

```python
2 % 2 == 0  # True
4 % 2 == 0  # True

1 % 2 == 0  # False
3 % 2 == 0  # False
```

---

## 7. 조건식을 하나씩 계산해보기

조건은 다음과 같다.

```python
(amount // 1000) % 2 == 0
```

### amount = 1000

```python
(1000 // 1000) % 2
= 1 % 2
= 1
```

따라서:

```python
1 == 0
```

→ `False` → 제외

---

### amount = 2000

```python
(2000 // 1000) % 2
= 2 % 2
= 0
```

따라서:

```python
0 == 0
```

→ `True` → 선택

그리고 선택되었으므로:

```python
2000 * 3
= 6000
```

---

### amount = 3000

```python
(3000 // 1000) % 2
= 3 % 2
= 1
```

따라서:

```python
1 == 0
```

→ `False` → 제외

---

### amount = 4000

```python
(4000 // 1000) % 2
= 4 % 2
= 0
```

따라서:

```python
0 == 0
```

→ `True` → 선택

그리고:

```python
4000 * 3
= 12000
```

---

## 8. 전체 과정을 표로 정리

| `amount` | `amount // 1000` | `% 2` | 조건 | `amount * 3` |
|---:|---:|---:|---|---:|
| 1000 | 1 | 1 | ❌ False | 제외 |
| 2000 | 2 | 0 | ✅ True | 6000 |
| 3000 | 3 | 1 | ❌ False | 제외 |
| 4000 | 4 | 0 | ✅ True | 12000 |

따라서 최종 결과는:

```python
[6000, 12000]
```

---

## 9. 가장 중요한 공식

리스트 내포를 볼 때 다음 형태를 먼저 찾으면 된다.

```python
[변환할 값 for 변수 in 리스트 if 조건]
```

이번 예제에 적용하면:

```text
[ amount * 3    for amount in base_deposits    if 조건 ]
      ↓                    ↓                      ↓
  무엇을 넣나?        무엇을 하나씩 꺼내나?       어떤 값만?
```

즉:

```python
[amount * 3 for amount in base_deposits if (amount // 1000) % 2 == 0]
```

은

> **`base_deposits`에서 하나씩 꺼내고 → 조건에 맞는 값만 골라서 → 3배한 결과를 새로운 리스트로 만들어라.**

라는 뜻이다.

---

## 10. 한 줄 요약

```python
[변환할 값 for 변수 in 리스트 if 조건]
```

**리스트에서 하나씩 꺼내기 → 조건 확인하기 → 조건이 맞으면 변환해서 새 리스트에 넣기**

이 순서로 이해하면 리스트 내포를 쉽게 해석할 수 있다.
