---
title: "[Python] 클래스 - class, self, __init__ 쉽게 이해하기"
date: 2026-10-06T07:18:29.370Z
tags: ["python"]
velog_slug: Python-06.-클래스-class-self-init-쉽게-이해하기
---
# 클래스 - class, self, \_\_init\_\_ 쉽게 이해하기

클래스를 처음 배우면 이런 생각이 든다.

> "`self`는 뭐고 `__init__`은 또 뭐지? 그냥 함수 쓰면 안 돼?"

나도 그랬다. 그래서 이번 글에서는 어려운 용어는 최대한 빼고, **붕어빵**과 **계산기**로 클래스를 정리해 본다.

> 실습 환경: VS Code + Jupyter Notebook (Python 3.14)

---

## 0. 한눈에 보기

| 용어 | 비유 | 한 줄 설명 |
|---|---|---|
| 클래스 `class` | **붕어빵 틀** | 물건을 만드는 설계도 |
| 객체(인스턴스) | **붕어빵** | 틀로 찍어 낸 진짜 물건 |
| 속성 | 붕어빵 **속 재료** | 객체가 기억하는 값 |
| 메서드 | 붕어빵이 할 수 있는 **행동** | 클래스 안에 있는 함수 |
| `__init__` | 반죽을 붓는 **첫 단계** | 객체가 태어날 때 자동으로 실행 |
| `self` | **"나 자신"** | 지금 이 객체를 가리키는 말 |

- 이 표만 기억해도 절반은 끝이다. 하나씩 보자.

---

## 1. 클래스와 객체 : 붕어빵 틀과 붕어빵

붕어빵 틀이 하나 있으면 붕어빵을 몇 개든 찍어 낼 수 있다.

- **붕어빵 틀** = 클래스 (설계도)
- **붕어빵** = 객체 (진짜 물건)

틀 자체는 먹을 수 없다. 틀로 **찍어 낸 붕어빵**을 먹는 거다.
클래스도 마찬가지다. 클래스를 만들었으면, 그걸로 **객체를 찍어 내야** 쓸 수 있다.

```python
class Bread:        # 붕어빵 틀 만들기
    pass            # 아직 내용은 비워 둠

a = Bread()         # 붕어빵 1개 찍기
b = Bread()         # 붕어빵 1개 더 찍기
```

> 💡 클래스 이름 뒤에 괄호 `()`를 붙이면 객체가 하나 만들어진다.

---

## 2. 계산기 클래스 살펴보기

이제 진짜 예제를 보자. **값을 기억하는 계산기**다.

```python
class Calculator:

    def __init__(self):
        self.result = 0

    def add(self, num):
        self.result += num
        return self.result

    def sub(self, num):
        self.result -= num
        return self.result
```

사용해 보면 이렇다.

```python
cal = Calculator()    # 계산기 한 대 만들기

print(cal.add(10))    # 10   (0 + 10)
print(cal.add(5))     # 15   (10 + 5)
print(cal.sub(3))     # 12   (15 - 3)
```

신기한 점은 **이전 결과를 기억한다**는 거다.
`add(5)`를 했을 때 0이 아니라 **10에서 시작**해서 15가 나왔다.

계산기에 비유하면 이렇다.

| 코드 | 계산기에서 |
|---|---|
| `Calculator` | 계산기 설계도 |
| `cal` | 내 손에 있는 계산기 한 대 |
| `self.result` | 계산기 **화면**에 떠 있는 숫자 |
| `add`, `sub` | **+ 버튼**, **- 버튼** |

---

## 3. \_\_init\_\_ : 태어날 때 하는 준비

```python
def __init__(self):
    self.result = 0
```

`__init__`은 객체가 **만들어지는 순간 자동으로 딱 한 번** 실행된다.

계산기 전원을 켜면 화면에 `0`이 뜨는 것처럼, `Calculator()`라고 쓰는 순간 `result`를 0으로 맞춰 준다.

- 이름 앞뒤로 밑줄이 **두 개씩** 붙는다: `__init__`
- 직접 부르지 않아도 된다. `Calculator()`라고 쓰면 알아서 실행된다.

### \_\_init\_\_이 없으면?

```python
class Calculator:
    def add(self, num):
        self.result += num
        return self.result

cal = Calculator()
cal.add(10)
```

```
AttributeError: 'Calculator' object has no attribute 'result'
```

"`result`가 없다"는 에러가 난다. 화면에 숫자를 띄워 둔 적이 없는데 거기에 10을 더하려고 했기 때문이다.

> 💡 `__init__` = 객체가 태어날 때 **필요한 준비물을 챙겨 주는 곳**

---

## 4. self : "나 자신"

클래스에서 가장 헷갈리는 게 `self`다. 계산기를 **두 대** 만들어 보면 바로 이해된다.

```python
cal1 = Calculator()
cal2 = Calculator()

cal1.add(10)
cal2.add(100)

print(cal1.result)   # 10
print(cal2.result)   # 100
```

두 계산기의 숫자가 **섞이지 않는다.** 이게 `self` 덕분이다.

- `cal1.add(10)`을 부르면 → `self`는 **cal1**
- `cal2.add(100)`을 부르면 → `self`는 **cal2**

그래서 `self.result`는 **"내 화면의 숫자"**라는 뜻이 된다.

```python
result += num        # ❌ 누구의 result인지 모름
self.result += num   # ✅ 나(이 계산기)의 result
```

### 왜 첫 번째 자리에 self를 꼭 써야 할까?

우리가 이렇게 쓰면

```python
cal.add(10)
```

파이썬은 속으로 이렇게 바꿔서 실행한다.

```python
Calculator.add(cal, 10)   # cal(나 자신)을 첫 번째로 몰래 넣어 줌
```

그래서 메서드를 만들 때 **첫 번째 자리에 그걸 받을 칸**이 필요하다. 그게 `self`다.

self를 빼먹으면 이런 에러가 난다.

```
TypeError: add() takes 1 positional argument but 2 were given
```

"1개 받기로 했는데 2개가 왔다" = 파이썬이 몰래 넣어 준 `cal`을 받을 칸이 없다는 뜻이다.

| 언제 | self를 쓰나? | 예 |
|---|---|---|
| 메서드를 **만들 때** | ✅ 꼭 쓴다 | `def add(self, num):` |
| 메서드를 **부를 때** | ❌ 안 쓴다 | `cal.add(10)` |

---

## 5. 그럼 클래스는 왜 쓸까?

솔직히 계산 몇 번 하는 정도면 **함수만으로도 충분하다.**

클래스가 빛나는 건 **"값을 기억하면서 여러 기능을 쓰는 물건"을 여러 개 만들 때**다.

- 은행 계좌 100개 (각자 잔액을 기억)
- 게임 캐릭터 10명 (각자 체력, 레벨을 기억)
- 계산기 여러 대 (각자 결과를 기억)

틀 하나만 잘 만들어 두면, 붕어빵 찍듯이 몇 개든 만들 수 있다.

---

여기서부터는 수업 시간에 직접 작성한 코드로 문법을 하나씩 정리해 본다.

## 6. 실습 1 : 가상 계좌 만들기 (객체는 서로 독립)

계산기와 똑같은 모양인데, 이번엔 **은행 계좌**다.

```python
class PracticeAccount:
    def __init__(self):
        self.balance = 0          # 계좌를 처음 만들면 잔액 0원

    def deposit(self, amount):    # 입금
        self.balance += amount
        return self.balance

    def withdraw(self, amount):   # 출금
        self.balance -= amount
        return self.balance
```

계좌를 **두 개** 만들어 보자.

```python
account_a = PracticeAccount()
account_b = PracticeAccount()

print("A 입금", account_a.deposit(30000))      # 30000
print("A 추가 입금", account_a.deposit(40000))  # 70000
print("A 출금", account_a.withdraw(40000))     # 30000
print("B 입금", account_b.deposit(40000))      # 40000

print("서로 독립된 잔액:", account_a.balance, account_b.balance)
```

```
서로 독립된 잔액: 30000 40000
```

- A에 입금해도 B의 잔액은 그대로다. 각자 **자기 `self.balance`**를 갖고 있기 때문이다.
- `account_a.balance`처럼 **`객체.속성`**으로 값을 바로 꺼내 볼 수도 있다.

> ⚠️ **Jupyter 주의**: 입금 셀만 여러 번 실행하면 잔액이 계속 쌓인다. 처음부터 다시 하고 싶으면 **객체를 만드는 셀(`PracticeAccount()`)부터 다시 실행**해야 0원으로 돌아간다.
> 실제로 나도 셀을 여러 번 돌렸다가 첫 입금 결과가 `130000`으로 나와서 한참 헤맸다.

---

## 7. 실습 2 : setdata()로 값 넣기 (\_\_init\_\_ 없이)

```python
class DepositPair:
    def setdata(self, first, second):
        self.first = first
        self.second = second

    def add(self):
        return self.first + self.second
```

```python
# 30000, 40000 값을 더하기
pair = DepositPair()           # 객체 만들기
pair.setdata(30000, 40000)     # 값 넣기
print(pair.add())              # 70000
```

- `__init__`이 없어도 **문법적으로는 문제없다.**
- 대신 `setdata()`가 `__init__` 역할을 대신한다. 그래서 **`setdata()`를 먼저 불러야** 한다.
- `setdata()`를 깜빡하고 `add()`부터 부르면 `AttributeError`가 난다. (3장에서 본 그 에러)

---

## 8. 실습 3 : \_\_init\_\_ + setdata() 같이 쓰기

위 문제를 해결하려면 `__init__`에서 **처음 값을 미리 0으로** 넣어 두면 된다.

```python
class DepositPair1:
    def __init__(self):
        self.first = 0             # 기본값 0
        self.second = 0

    def setdata(self, first, second):
        self.first = first
        self.second = second

    def add(self):
        return self.first + self.second
```

```python
pair = DepositPair1()
print(pair.add())             # 0      ← setdata 전이어도 에러 없음!

pair.setdata(30000, 40000)
print(pair.add())             # 70000

pair.setdata(3000, 4000)      # 값은 언제든 다시 바꿀 수 있다
print(pair.add())             # 7000
```

| 메서드 | 역할 |
|---|---|
| `__init__` | 태어날 때 **기본값**을 준비 (한 번만, 자동) |
| `setdata` | 나중에 **원하는 값으로 바꾸기** (몇 번이든, 직접 호출) |

---

## 9. 실습 4 : \_\_init\_\_에 값 받기 (금융 계산기)

이번엔 `__init__`이 **값을 직접 받는다.**

```python
class FinanceCalculator:
    def __init__(self, first, second):   # 만들 때 값 2개를 받음
        self.first = first
        self.second = second

    def setdata(self, first, second):
        self.first = first
        self.second = second

    def add(self):
        return self.first + self.second

    def sub(self):
        return self.first - self.second

    def mul(self):
        return self.first * self.second

    def div(self):
        return self.first / self.second
```

### 객체 만들 때 괄호 안에 값을 넣는다

```python
cal = FinanceCalculator(50000, 3)   # 괄호 안 값이 그대로 __init__으로 들어감

print("가상 단가 x 수량:", cal.mul())          # 150000
print(f"가상 단가 / 건수: {cal.div():.1f}")    # 16666.7
```

`__init__(self, first, second)`이면 만들 때 **값 2개가 꼭 필요**하다. 빼먹으면 이런 에러가 난다.

```python
cal = FinanceCalculator()
# TypeError: FinanceCalculator.__init__() missing 2 required positional arguments: 'first' and 'second'
```

### 자주 한 실수 ① : 클래스로 바로 메서드 부르기

```python
FinanceCalculator.setdata(50000, 3)   # ❌ 붕어빵 틀에 직접 반죽을 넣는 것
cal.setdata(50000, 3)                 # ✅ 객체로 부르기
```

틀(클래스)로 부르면 `self` 자리에 `50000`이 들어가 버려서 에러가 난다. **메서드는 항상 객체로 부른다.**

### 자주 한 실수 ② : f-string 밖에서 서식 쓰기

```python
print("가상 단가 / 건수:", cal.div().1f)       # ❌ SyntaxError: invalid decimal literal
print(f"가상 단가 / 건수: {cal.div():.1f}")    # ✅
```

`:.1f` 같은 서식은 **f-string의 `{ }` 안에서만** 쓸 수 있다.

| 서식 | 16666.666... 출력 결과 |
|---|---|
| `{값:.1f}` | `16666.7` (소수점 첫째 자리) |
| `{값:.2f}` | `16666.67` (소수점 둘째 자리) |
| `{값:,}` | 천 단위 쉼표 (`150000` → `150,000`) |
| `{값:,.1f}` | `16,666.7` |

### 알아 두면 좋은 점

- `/` 나눗셈 결과는 항상 **소수(float)**다. `6 / 3` → `2.0`
- **0으로 나누면** `ZeroDivisionError`가 난다. `FinanceCalculator(50000, 0).div()` → 에러

---

## 10. 실습 5 : 클래스 상속 (inheritance)

`FinanceCalculator`에 **성장계수 기능**을 하나 더 넣고 싶다.
그런데 원래 클래스를 고치거나, 처음부터 다시 다 쓰기는 번거롭다.

이럴 때 쓰는 게 **상속**이다. 붕어빵으로 치면 이렇다.

- 기존 **팥 붕어빵 틀**을 그대로 가져와서
- **슈크림 칸만 하나 더 붙인** 새 틀을 만드는 것

### 상속 문법 : 클래스 이름 옆 괄호에 부모 클래스

```python
class GrowthCalculator(FinanceCalculator):   # FinanceCalculator를 물려받음
    def growth_factor(self):                 # 성장계수 (새로 추가한 기능)
        return self.first ** self.second
```

| 용어 | 이 예제에서 | 뜻 |
|---|---|---|
| 부모 클래스 | `FinanceCalculator` | 기능을 **물려주는** 클래스 |
| 자식 클래스 | `GrowthCalculator` | 기능을 **물려받는** 클래스 |

- 자식 클래스에는 `growth_factor()` 하나만 썼다.
- 그런데 부모의 `__init__`, `setdata`, `add`, `sub`, `mul`, `div`를 **전부 그대로 쓸 수 있다.**

### 사용해 보기

```python
extended = GrowthCalculator(10000, 20000)    # 부모의 __init__이 그대로 실행됨
print("상속 받은 add(가상입금액 합계):", extended.add())

extended.setdata(1.05, 2)                    # 부모의 setdata로 값 바꾸기
print("추가한 growth_factor:", extended.growth_factor())
```

```
상속 받은 add(가상입금액 합계): 30000
추가한 growth_factor: 1.1025
```

- `GrowthCalculator` 안에는 `__init__`도 `add`도 없는데 **잘 동작한다.** 부모한테 물려받았기 때문이다.
- `growth_factor()`는 **자식에게만** 있다. `FinanceCalculator`로 만든 객체에서는 쓸 수 없다.

### `**` : 거듭제곱

```python
1.05 ** 2    # 1.05 × 1.05 = 1.1025
```

- `a ** b` = a를 b번 곱하기
- 금리 5%로 2년 동안 불리면 원금의 **1.1025배**가 된다는 뜻이다. (복리 성장계수)

### 메서드 찾는 순서

`extended.add()`를 부르면 파이썬은 이렇게 찾는다.

1. 먼저 **자식(`GrowthCalculator`)**에서 `add`를 찾는다 → 없다
2. 그다음 **부모(`FinanceCalculator`)**에서 찾는다 → 있다! 실행

### 헷갈렸던 점 : `"setdata": Unknown word.` 경고

VS Code에서 `setdata`에 물결 밑줄과 함께 `Unknown word`가 뜬다. **파이썬 에러가 아니다.**
맞춤법 검사 확장(Code Spell Checker)이 사전에 없는 영어 단어라서 표시한 것뿐이니 실행에는 아무 영향이 없다.

---

## 11. 메서드 오버라이딩 (overriding) : 물려받은 기능 바꾸기

10장에서는 부모에게 **없는** 기능을 자식에 **추가**했다.
이번에는 부모에게 **이미 있는** 기능을 자식에서 **바꿔** 본다.

### 문제 상황 : 0으로 나누면 프로그램이 멈춘다

부모 클래스 `FinanceCalculator`의 나눗셈은 이렇게 생겼다.

```python
def div(self):
    return self.first / self.second
```

여기서 `second`가 **0**이면 어떻게 될까? 수학에서 0으로는 나눌 수 없다. 파이썬도 마찬가지다.

```python
FinanceCalculator(50000, 0).div()
```

```
ZeroDivisionError: division by zero
```

에러가 나면 프로그램이 **그 자리에서 멈춘다.** 계산기로 0을 나눴더니 계산기가 꺼져 버리는 것과 같다.

### 해결 방법 두 가지

| 방법 | 내용 | 문제점 |
|---|---|---|
| A. 부모를 직접 고친다 | `FinanceCalculator`의 `div`를 수정 | 부모를 이미 다른 곳에서 쓰고 있으면 거기까지 바뀐다 |
| B. 자식에서 다시 만든다 | 자식 클래스에 **같은 이름**의 `div`를 새로 작성 | 없음. 부모는 그대로 둔다 |

B 방법이 바로 **오버라이딩(overriding)**이다.

> 📒 **비유 : 형이 물려준 게임 공략집**
> 공략집은 그대로 물려받는데, **보스전 페이지 한 장만** 내가 새로 써서 그 위에 **포스트잇으로 덮어 붙인다.**
> 다른 페이지는 형 공략집을 그대로 보고, 보스전에서만 내 포스트잇을 본다.
> 형 공략집 원본은 **하나도 안 바뀐다.**

### 오버라이딩 코드

```python
class SafeCalculator(FinanceCalculator):   # FinanceCalculator를 물려받음
    def div(self):                         # 부모와 같은 이름 → 부모의 div를 덮어씀
        if self.second == 0:               # 나누는 수가 0이면
            return 0                       # 나눗셈을 하지 않고 0을 돌려줌
        return self.first / self.second    # 0이 아니면 평소처럼 나눗셈
```

### 한 줄씩 풀이

```python
class SafeCalculator(FinanceCalculator):
```

- `SafeCalculator`라는 새 클래스를 만들고, 괄호 안의 `FinanceCalculator`를 **전부 물려받는다.**
- 그래서 `__init__`, `setdata`, `add`, `sub`, `mul`은 따로 안 써도 다 쓸 수 있다.

```python
    def div(self):
```

- 부모에게도 `div`가 있는데, 자식에서 **똑같은 이름**으로 다시 만들었다.
- 이름이 같으니 부모의 `div` 위에 **포스트잇을 덮어 붙인** 셈이다.
- 이름이 **한 글자라도 다르면** (`divide`, `Div` 등) 덮어쓰기가 아니라 **새 메서드 추가**가 돼 버린다.

```python
        if self.second == 0:
            return 0
```

- "나누는 수(`second`)가 0이야?"를 확인한다.
- `==`는 **같은지 비교**하는 기호다. `=` 하나는 값을 넣는 거라서 다르다.
- 0이면 나눗셈을 **아예 하지 않고** 바로 0을 돌려준다.
- `return`을 만나면 메서드는 **거기서 바로 끝난다.** 그래서 아래 줄은 실행되지 않는다.

```python
        return self.first / self.second
```

- `second`가 0이 **아닐 때만** 여기까지 내려온다. 그때는 부모와 똑같이 나눗셈을 한다.

### 실행해 보기

```python
safe = SafeCalculator(50000, 0)
print(safe.div())    # 0         ← 에러 대신 0
```

```python
safe = SafeCalculator(50000, 4)
print(safe.div())    # 12500.0   ← 0이 아니니까 평소처럼 나눔
print(safe.add())    # 50004     ← 자식에 add가 없으니 부모의 add
print(safe.mul())    # 200000    ← 이것도 부모의 mul
```

### 파이썬은 어떤 div를 쓸까? : 자식부터 찾는다

`safe.div()`를 부르면 파이썬은 이 순서로 찾는다.

1. **자식(`SafeCalculator`)에 `div`가 있나?** → 있다! 이걸 실행
2. 이미 찾았으니 부모 쪽은 **아예 보러 가지 않는다.**

`safe.add()`라면?

1. **자식(`SafeCalculator`)에 `add`가 있나?** → 없다
2. **부모(`FinanceCalculator`)에 `add`가 있나?** → 있다! 이걸 실행

| 부른 메서드 | 자식에 있나? | 실제로 실행되는 것 |
|---|---|---|
| `div()` | ✅ 있음 | **자식이 새로 만든 div** |
| `add()` | ❌ 없음 | 부모의 add |
| `mul()` | ❌ 없음 | 부모의 mul |
| `__init__` | ❌ 없음 | 부모의 `__init__` |

### 부모는 바뀌었을까?

```python
FinanceCalculator(50000, 0).div()   # 여전히 ZeroDivisionError
```

**안 바뀌었다.** 포스트잇은 **자식 클래스에만** 붙였고, 부모 클래스는 원래 그대로다.

- `FinanceCalculator`로 만든 객체 → 부모의 `div` (0이면 에러)
- `SafeCalculator`로 만든 객체 → 자식의 `div` (0이면 0)

> 💡 9장에서 본 `ZeroDivisionError`를 **부모 클래스를 한 줄도 건드리지 않고** 고쳤다. 이게 오버라이딩의 장점이다.

### 상속(추가) vs 오버라이딩(바꾸기)

| | 상속으로 추가 (`growth_factor`) | 오버라이딩 (`div`) |
|---|---|---|
| 하는 일 | 부모에 **없는** 기능을 **추가** | 부모에 **있는** 기능을 **바꿈** |
| 메서드 이름 | 새 이름 (`growth_factor`) | 부모와 **같은 이름** (`div`) |
| 부모 클래스 | 그대로 | 그대로 |
| 비유 | 공략집에 **새 페이지 추가** | 기존 페이지에 **포스트잇 덮기** |

> 💡 **오버라이딩 = 부모 것을 물려받되, 마음에 안 드는 메서드 하나만 같은 이름으로 다시 만들어 덮어쓰기.**
> 파이썬은 항상 **자식부터** 찾기 때문에 자식이 만든 것이 먼저 쓰인다.

---

## 12. 문법 모음

지금까지 쓴 문법을 한 표로 모았다.

| 문법 | 예시 | 뜻 |
|---|---|---|
| 클래스 만들기 | `class PracticeAccount:` | 설계도 시작. 이름은 **대문자로 시작** |
| 생성자 | `def __init__(self):` | 객체가 태어날 때 자동 실행 |
| 값 받는 생성자 | `def __init__(self, first, second):` | 만들 때 값을 받아서 초기화 |
| 메서드 | `def deposit(self, amount):` | 클래스 안의 함수. 첫 자리는 `self` |
| 속성 저장 | `self.balance = 0` | 객체가 기억할 값 |
| 더해서 저장 | `self.balance += amount` | `self.balance = self.balance + amount` |
| 빼서 저장 | `self.balance -= amount` | `self.balance = self.balance - amount` |
| 값 돌려주기 | `return self.balance` | 메서드 결과를 밖으로 보냄 |
| 객체 만들기 | `account_a = PracticeAccount()` | 틀로 붕어빵 찍기 |
| 값 넣어 만들기 | `cal = FinanceCalculator(50000, 3)` | 괄호 안 값 → `__init__` |
| 메서드 부르기 | `account_a.deposit(30000)` | `self`는 안 씀 |
| 속성 꺼내기 | `account_a.balance` | 객체가 기억하는 값 보기 |
| f-string 서식 | `f"{cal.div():.1f}"` | 소수점 첫째 자리까지 |
| 상속 | `class GrowthCalculator(FinanceCalculator):` | 부모 클래스의 기능을 물려받음 |
| 거듭제곱 | `self.first ** self.second` | `1.05 ** 2` → `1.1025` |
| 오버라이딩 | 자식에서 `def div(self):` 다시 작성 | 부모와 같은 이름 → 자식 것이 먼저 쓰임 |
| 같은지 비교 | `if self.second == 0:` | `==`는 비교, `=`는 값 넣기 |

---

## 13. 정리

- **클래스** = 붕어빵 틀(설계도), **객체** = 찍어 낸 붕어빵
- `객체 = 클래스이름()` 으로 객체를 만든다.
- **`__init__`** = 객체가 태어날 때 자동 실행. 처음 값을 준비한다.
- **`self`** = "나 자신". 내 값(`self.result`)을 찾을 때 쓴다.
- 메서드를 **만들 때는** 첫 자리에 `self`를 쓰고, **부를 때는** 안 쓴다.
- 객체끼리는 **서로 독립**이다. A 계좌에 입금해도 B 계좌는 그대로다.
- `__init__`이 값을 받으면 → **만들 때 괄호 안에 값**을 넣어야 한다.
- 메서드는 **클래스가 아니라 객체로** 부른다.
- **상속** = `class 자식(부모):` 로 부모의 기능을 그대로 물려받고, 필요한 기능만 추가한다.
- 부모와 같은 이름의 메서드를 자식에서 만들면 자식 것이 쓰인다. (**오버라이딩**)

```python
# 이것만 기억하자
class 클래스이름:
    def __init__(self):       # 태어날 때 준비
        self.값 = 처음값

    def 기능(self, 입력):      # 버튼
        self.값 = ...          # 내 값을 바꿈
        return self.값

객체 = 클래스이름()
객체.기능(입력)
```

b