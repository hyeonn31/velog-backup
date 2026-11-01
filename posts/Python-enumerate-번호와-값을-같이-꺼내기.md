---
title: "[Python] enumerate() - 번호와 값을 같이 꺼내기"
date: 2026-10-02T06:23:42.146Z
tags: ["python"]
velog_slug: Python-enumerate-번호와-값을-같이-꺼내기
---
# enumerate() - 번호와 값을 같이 꺼내기

for문으로 리스트를 돌다 보면 이런 생각이 들 때가 있다.

> "지금 꺼낸 값이 **몇 번째** 값이지?"

예를 들어 5일 동안의 수익률이 있을 때, 그냥 값만 보는 게 아니라 **"3일차 수익률은 1%"** 처럼 몇 일차인지도 같이 알고 싶을 때가 있다.
이럴 때 쓰는 함수가 바로 **`enumerate()`** 다.

> 실습 환경: VS Code + Jupyter Notebook (Python 3.14)

---

## 0. 한 줄 요약

| 함수 | 하는 일 | 꺼내 주는 것 |
|---|---|---|
| `enumerate(리스트)` | 리스트를 돌면서 **번호표**를 같이 붙여 줌 | `(번호, 값)` 한 쌍 |

- 비유하자면 **은행 번호표 기계**다. 줄 선 사람(값)에게 순서대로 번호표를 하나씩 쥐여 준다.
- 이 표만 기억해도 절반은 끝났다. 이제 하나씩 보자.

---

## 1. enumerate 없이 for문을 돌리면

```python
daily_returns = [0.03, -0.02, 0.01, -0.01, 0.04]

for r in daily_returns:
    print(r)
```

```
0.03
-0.02
0.01
-0.01
0.04
```

값은 잘 나오는데, **몇 번째 값인지는 알 수 없다.**

### 번호를 직접 세려면?

```python
day = 1
for r in daily_returns:
    print(day, r)
    day += 1
```

- 번호 변수 `day`를 따로 만들고
- 반복할 때마다 `day += 1`로 직접 늘려 줘야 한다.

잘 되긴 하지만 귀찮고, `day += 1`을 깜빡하면 번호가 안 바뀌는 실수도 생긴다.

---

## 2. enumerate 사용하기

```python
for i, r in enumerate(daily_returns):
    print(i, r)
```

```
0 0.03
1 -0.02
2 0.01
3 -0.01
4 0.04
```

`enumerate`는 매번 **`(번호, 값)`** 한 쌍을 꺼내 준다.
그 한 쌍이 `i`와 `r`에 나뉘어 들어가는 것이다.

```python
for i, r in enumerate(daily_returns):
#   ↑  ↑
#  번호 값
```

> 💡 번호를 직접 셀 필요가 없다. `enumerate`가 대신 세 준다.

---

## 3. start=1 : 번호를 1부터 시작하기

파이썬은 번호를 **0부터** 센다. 그래서 위 결과도 0부터 시작했다.
그런데 "0일차"는 어색하다. 이럴 때 **`start=1`** 을 붙인다.

```python
for day, r in enumerate(daily_returns, start=1):
    print(day, r)
```

```
1 0.03
2 -0.02
3 0.01
4 -0.01
5 0.04
```

| 쓰는 법 | 번호 시작 |
|---|---|
| `enumerate(리스트)` | 0부터 |
| `enumerate(리스트, start=1)` | 1부터 |
| `enumerate(리스트, start=10)` | 10부터 |

---

## 4. 순서가 중요하다 (이름은 상관없다)

처음에 헷갈리기 쉬운 부분이다.

```python
for day, r in enumerate(daily_returns, start=1):
```

- **첫 번째 자리** → 항상 **번호**
- **두 번째 자리** → 항상 **값**

파이썬은 변수 **이름**을 보고 판단하지 않는다. 그냥 **앞 자리에 번호, 뒷 자리에 값**을 넣을 뿐이다.

```python
for a, b in enumerate(daily_returns, start=1):
    print(a, b)   # 결과는 위와 똑같다
```

`day`, `r`이라는 이름은 사람이 읽기 쉽게 붙인 것일 뿐이다.

### 순서를 바꿔 쓰면?

```python
for day, r in enumerate(daily_returns, start=1):
    print(f"{r}일차 수익률: {day:.2%}")
```

```
0.03일차 수익률: 100.00%
```

"0.03일차"에 "100%"... 완전히 엉망이 된다. **번호 자리와 값 자리를 헷갈리지 말자.**

---

## 5. 실전 예제 : 수익률이 양수인 날 찾기

`enumerate` + `if`를 같이 쓰면 **조건에 맞는 값이 몇 번째인지** 쉽게 찾을 수 있다.

```python
daily_returns = [0.03, -0.02, 0.01, -0.01, 0.04]

for day, r in enumerate(daily_returns, start=1):
    if r > 0:
        print(f"{day}일차 수익률: {r:.2%}")
```

```
1일차 수익률: 3.00%
3일차 수익률: 1.00%
5일차 수익률: 4.00%
```

> 💡 `:.2%` 는 **100을 곱하고 소수점 둘째 자리까지 + % 기호**를 붙여 주는 서식이다. `0.03` → `3.00%`

### 리스트 컴프리헨션으로 한 줄에

```python
positive_days = [day for day, r in enumerate(daily_returns, start=1) if r > 0]
print(positive_days)
```

```
[1, 3, 5]
```

---

## 6. 정리

- `enumerate(리스트)` → 반복할 때 **`(번호, 값)`** 을 같이 꺼내 준다.
- 번호는 기본 **0부터**, `start=1`을 주면 **1부터** 시작한다.
- `for 번호, 값 in enumerate(...)` → **순서**가 중요하고, 이름은 자유다.
- 번호 변수를 직접 만들고 `+= 1` 할 필요가 없어서 코드가 짧고 실수가 줄어든다.

```python
# 이것만 기억하자
for 번호, 값 in enumerate(리스트, start=1):
    print(번호, 값)
```
