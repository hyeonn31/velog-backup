---
title: "[Python] 예외처리 제대로 이해하기"
date: 2026-10-07T01:45:50.397Z
tags: ["python", "예외처리", "파이썬기초"]
velog_slug: Python-예외처리-제대로-이해하기
---


# 파이썬 예외처리 정리

데이터 공부를 하면서 파이썬 코드를 꽤 많이 돌리고 있는데, 제일 자주 보는 화면이 빨간 에러 메시지다. 처음엔 그냥 에러가 나면 고치고, 또 나면 또 고치는 식이었는데 그러다 보니 데이터 하나 이상한 거 때문에 몇십 분 돌린 코드가 중간에 멈추는 일이 생겼다. 그래서 이번에 예외처리를 제대로 한 번 정리해 봤다.

나처럼 처음 보는 사람도 이해할 수 있게 최대한 쉽게 써보려고 했다.

## 에러에도 종류가 있더라

처음에는 에러가 다 똑같은 건 줄 알았는데, 크게 두 가지로 나뉜다.

하나는 문법 오류다. 괄호를 안 닫았다거나, 콜론을 빼먹었다거나 하는 것들.

```python
print("안녕하세요"
```

이건 파이썬이 코드를 읽는 단계에서 이미 "이거 문장이 이상한데?" 하고 실행 자체를 안 한다. 그래서 예외처리로 어떻게 할 수 있는 게 아니고, 그냥 코드를 고쳐야 한다.

다른 하나가 오늘 정리할 예외다. 문장은 멀쩡한데 실행하다가 문제가 생기는 경우.

```python
print(10 / 0)
```

```
ZeroDivisionError: division by zero
```

코드 자체는 틀린 데가 없다. 근데 0으로 나누는 건 수학적으로 안 되니까 실행하는 순간 멈춰버린다.

나는 이걸 라면 끓이는 거에 비유해서 이해했다. 레시피(코드)는 완벽한데 막상 끓이려고 보니 찬장에 라면이 없는 상황. 사람은 "아 없네, 편의점 가야겠다" 하고 알아서 대처하는데, 컴퓨터는 미리 알려주지 않으면 그 자리에서 그냥 멈춘다. 그 "없으면 이렇게 해"를 미리 알려주는 게 예외처리다.

내가 자주 본 예외들은 이 정도였다.

- `ZeroDivisionError` : 0으로 나눴을 때
- `ValueError` : `int("사과")`처럼 값이 이상할 때
- `TypeError` : `"나이: " + 14`처럼 문자랑 숫자를 그냥 더할 때
- `KeyError` : 딕셔너리에 없는 키를 찾을 때
- `IndexError` : 리스트 길이보다 큰 번호를 넣었을 때
- `FileNotFoundError` : 없는 파일을 열려고 할 때

이름만 봐도 대충 뭐가 문제인지 감이 와서 생각보다 친절하다.

## 에러 메시지 읽는 법

솔직히 예전엔 에러 메시지가 길게 뜨면 겁부터 났다. 근데 읽는 요령을 알고 나니까 오히려 고마운 존재가 됐다.

```
Traceback (most recent call last):
  File "main.py", line 3, in <module>
    age = int(text)
ValueError: invalid literal for int() with base 10: '열네살'
```

**맨 아래 줄부터 읽으면 된다.** 이게 제일 중요하다.

- `ValueError` → 값이 잘못됐구나
- `'열네살'` → "열네살"을 숫자로 바꾸려다가 실패했구나
- `line 3` → 3번째 줄이구나

위에 길게 써 있는 건 "어떤 경로로 여기까지 왔는지"라서, 처음엔 맨 아래 한두 줄만 봐도 충분하다.

## try / except 기본

서커스에서 공중그네 탈 때 밑에 그물 쳐두는 거랑 비슷하다. 떨어질 수 있는 구간에 그물을 쳐두는 것.

```python
text = input("나이를 입력하세요: ")

try:
    age = int(text)
    print(f"내년에는 {age + 1}살이네요!")
except ValueError:
    print("숫자로 입력해 주세요.")
```

이해하는 데 제일 도움이 됐던 건 실제로 코드가 어떤 순서로 실행되는지 따라가 보는 거였다.

"14"를 넣으면 `int("14")`가 잘 되니까 "내년에는 15살이네요!"가 나오고, except는 그냥 건너뛴다.

"열네살"을 넣으면 `int("열네살")`에서 에러가 난다. 여기서 중요한 게, **에러가 난 그 줄에서 바로 except로 점프한다는 것.** 그래서 그 아래 있는 print는 아예 실행이 안 된다. 나는 처음에 try 안에 있는 코드가 끝까지 다 실행되고 나서 except로 가는 줄 알았는데 아니었다.

에러 내용을 직접 보고 싶으면 `as`를 붙이면 된다.

```python
try:
    age = int("열네살")
except ValueError as e:
    print("문제가 생겼어요:", e)
```

except는 여러 개 쓸 수도 있다. 위에서부터 차례대로 "이 에러 맞아?" 하고 확인한다.

```python
try:
    numbers = [10, 20, 30]
    idx = int(input("몇 번째 숫자를 볼까요? "))
    print(100 / numbers[idx])
except ValueError:
    print("숫자를 입력해야 해요.")
except IndexError:
    print("그 번호에는 숫자가 없어요.")
```

똑같이 처리할 거면 괄호로 묶어도 된다.

```python
except (ValueError, IndexError):
    print("입력을 다시 확인해 주세요.")
```

## else랑 finally

try, except 말고도 두 개가 더 있다.

```python
try:
    age = int(input("나이: "))
except ValueError:
    print("숫자가 아니에요.")
else:
    print("잘 입력했어요!")
finally:
    print("프로그램을 마칠게요.")
```

- `else` : try에서 에러가 **안 났을 때만** 실행
- `finally` : 에러가 났든 안 났든 **무조건** 실행

finally는 놀이터에서 놀고 나서 장난감 정리하는 거라고 생각하니까 바로 외워졌다. 잘 놀았든 넘어져서 울었든 집에 가기 전엔 정리하니까. 프로그램에서는 파일 닫기 같은 마무리 작업을 여기에 넣는다.

else는 처음에 왜 필요한지 몰랐다. 그냥 try 안에 쓰면 되는 거 아닌가 싶었는데, try 안에 코드를 많이 넣으면 내가 예상 못 한 곳에서 난 에러까지 except가 잡아버린다. 그물을 너무 넓게 치면 엉뚱한 게 걸리는 거다. 그래서 에러 날 만한 줄만 try에 넣고, 성공한 다음에 할 일은 else로 빼는 게 깔끔하다고 한다.

## 예외에도 족보가 있다

이게 개인적으로 제일 "아 그래서 그랬구나" 했던 부분이다. 파이썬 예외들은 부모 자식 관계로 이어져 있다.

```
BaseException (제일 위 조상)
 ├── KeyboardInterrupt  (Ctrl+C 눌렀을 때)
 ├── SystemExit         (프로그램 끝내라는 신호)
 └── Exception          (평소에 다루는 에러들의 부모)
      ├── ValueError
      ├── TypeError
      ├── ZeroDivisionError
      └── LookupError
           ├── KeyError
           └── IndexError
```

부모를 잡으면 자식도 같이 잡힌다. `except LookupError:` 하나로 KeyError, IndexError 둘 다 잡히는 식.

그래서 순서를 조심해야 한다.

```python
try:
    ...
except Exception:
    print("뭔가 문제가 있어요")
except ValueError:
    print("값이 이상해요")   # 여기는 절대 안 옴
```

ValueError는 Exception의 자식이라 위에서 이미 잡혀버린다. 구체적인 걸 위에, 넓은 걸 아래에 써야 한다.

### bare except

정리하다가 처음 알게 된 용어다.

```python
try:
    ...
except:
    pass
```

이렇게 except 뒤에 아무것도 안 쓴 걸 bare except라고 부른다. bare가 "맨몸의"라는 뜻이라 이름 없이 맨몸으로 쓴 except라는 의미.

편해 보이는데 쓰면 안 되는 이유가 있다. 족보 맨 꼭대기인 BaseException까지 다 잡아버려서, Ctrl+C를 눌러도 프로그램이 안 꺼진다. 그리고 내가 낸 오타 같은 버그까지 조용히 넘어가 버려서 나중에 뭐가 문제인지 찾기가 엄청 힘들어진다. 넓게 잡고 싶어도 최소한 `except Exception:`으로 쓰고, 웬만하면 `except ValueError:`처럼 이름을 정확히 쓰는 게 좋다.

`pass`로 에러를 그냥 삼키는 것도 마찬가지다. 시험 틀렸는데 채점을 안 해주는 거랑 같아서 어디서 틀렸는지 영영 모르게 된다. 잡았으면 print라도 하나 남겨두자.

## raise : 내가 직접 에러 내기

파이썬은 모르는데 나는 문제라는 걸 아는 상황이 있다.

```python
def buy_snack(money, price):
    if money < price:
        raise ValueError("돈이 부족해요!")
    return money - price
```

1000원으로 1500원짜리를 사면 파이썬 입장에선 그냥 -500이 나올 뿐이다. 계산상 아무 문제 없으니까. 근데 현실에서 돈이 마이너스가 될 순 없으니 내가 직접 에러를 던지는 거다.

에러를 잡았다가 더 알아보기 쉬운 에러로 바꿔서 다시 던질 때는 `from`을 붙이면 원래 이유도 같이 남는다.

```python
try:
    score = int("구십")
except ValueError as e:
    raise RuntimeError("성적 파일 읽다가 실패") from e
```

"숙제 못 했어"보다 "숙제 못 했어, 교과서를 학교에 두고 와서"가 훨씬 도움이 되는 것처럼, `from e`가 그 "왜냐면"을 붙여준다.

## 나만의 예외 만들기

기본 예외만으로는 상황 설명이 애매할 때 직접 만들 수 있다. 생각보다 간단하다.

```python
class GameError(Exception):
    pass

class NotEnoughCoinsError(GameError):
    pass

class InventoryFullError(GameError):
    pass
```

```python
def buy_item(coins, price, bag_count):
    if coins < price:
        raise NotEnoughCoinsError("코인이 부족해요")
    if bag_count >= 10:
        raise InventoryFullError("가방이 꽉 찼어요")
    return coins - price

try:
    buy_item(coins=50, price=100, bag_count=3)
except NotEnoughCoinsError:
    print("코인을 더 모아오세요!")
except InventoryFullError:
    print("가방을 비워주세요!")
```

그냥 ValueError라고 했으면 무슨 문제인지 바로 안 보였을 텐데 이름만 봐도 상황이 그려진다. 그리고 둘 다 GameError 자식이라 `except GameError:` 한 줄로 한꺼번에 잡을 수도 있다. 앞에서 정리한 족보 개념이 여기서 쓰인다.

## with 쓰면 편하다

파일은 열면 꼭 닫아줘야 한다. 예외처리로만 하면 이렇게 된다.

```python
f = open("일기.txt", encoding="utf-8")
try:
    content = f.read()
finally:
    f.close()
```

근데 `with`를 쓰면 알아서 닫아준다.

```python
with open("일기.txt", encoding="utf-8") as f:
    content = f.read()
```

자동문 같은 느낌이다. 안에서 무슨 일이 있든 나오면 문이 닫혀 있다. 요즘 파일 다룰 땐 거의 이것만 쓴다.

## 먼저 확인할까, 일단 해볼까

에러를 피하는 스타일이 두 가지 있다는 것도 알게 됐다.

```python
scores = {"수학": 90, "영어": 85}

# 먼저 확인하기
if "과학" in scores:
    print(scores["과학"])

# 일단 해보기
try:
    print(scores["과학"])
except KeyError:
    print("과학 점수가 없어요")
```

친구 집 가기 전에 "가도 돼?" 물어보는 게 첫 번째, 일단 초인종 누르고 안 되면 돌아오는 게 두 번째다. 파이썬은 두 번째 방식을 꽤 좋아한다고 한다. 확인하고 실행하는 그 사이에 상황이 바뀔 수도 있어서. 그래도 실패가 자주 나는 상황이면 먼저 확인하는 쪽이 낫다고 하니까 정답이 정해져 있는 건 아닌 것 같다.

## (참고) Python 3.11에 추가된 것

아직 직접 쓸 일은 없었는데 정리하다 보니 알게 돼서 남겨둔다. 여러 작업을 동시에 돌리다 보면 에러가 한꺼번에 여러 개 날 수 있는데, 이걸 묶어서 처리하는 `ExceptionGroup`과 `except*`가 생겼다.

```python
try:
    raise ExceptionGroup("여러 문제", [ValueError("값 문제"), KeyError("키 문제")])
except* ValueError:
    print("값 문제 처리")
except* KeyError:
    print("키 문제 처리")
```

택배 상자에 여러 물건이 들어 있으면 옷은 옷장에, 책은 책장에 나눠 넣는 것처럼, 묶음 안에서 자기 담당만 꺼내서 처리한다.

에러에 메모를 붙이는 `add_note()`도 있다. 몇 번째 데이터에서 터졌는지 같은 걸 남길 수 있어서 이건 나중에 유용하게 쓸 것 같다.

```python
try:
    int("abc")
except ValueError as e:
    e.add_note("3번째 학생 점수 읽는 중이었음")
    raise
```

## 실제로 써먹은 패턴

처음에 말했던 "데이터 하나 때문에 전체가 멈추는 문제"는 이렇게 해결했다.

```python
scores = ["90", "85", "구십", "70", ""]
good = []
bad = []

for i, s in enumerate(scores):
    try:
        good.append(int(s))
    except ValueError:
        bad.append(i)

print("성공:", good)        # [90, 85, 70]
print("실패한 번호:", bad)   # [2, 4]
```

이상한 데이터는 따로 모아두고 나머지는 계속 처리한다. 데이터 정리할 때 진짜 자주 쓰게 될 것 같다.

## 정리하면서 느낀 점

정리하고 나니까 예외처리가 에러를 숨기는 기술이 아니라 "문제가 생기면 어떻게 할지 미리 정해두는 것"이라는 게 와닿았다. 내가 앞으로 지키려고 하는 건 이 정도다.

- try 안에는 에러 날 만한 줄만 넣기
- except 뒤에 예외 이름 꼭 쓰기
- 잡았으면 흔적 남기기 (pass로 넘기지 않기)
- 파일은 with로 열기

다음에는 이걸 실제 데이터 처리 코드에 적용해 보면서 로그 남기는 방법까지 정리해 볼 생각이다.

## 참고한 자료

- [Python 공식 튜토리얼 - Errors and Exceptions](https://docs.python.org/3/tutorial/errors.html)
- [Python 공식 문서 - Built-in Exceptions](https://docs.python.org/3/library/exceptions.html)
- [PEP 8 - Programming Recommendations](https://peps.python.org/pep-0008/#programming-recommendations)
- [PEP 654 - Exception Groups and except*](https://peps.python.org/pep-0654/)