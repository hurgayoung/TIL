# [0731] Python 8일차 - OOP (2)

Table of Contents

1. 상속

   1-1. 부모 클래스와 자식 클래스

   1-2. 메서드 오버라이딩

   1-3. 다중 상속

2. 에러와 예외

   2-1. 디버깅
   2-2. 에러
   2-3. 예외

3. 예외 처리

   3-1. try & except

   3-2. 복수 예외 처리

   3-3. else & finally

Objectives

- 클래스 상속의 개념과 장점을 설명할 수 있다.
- 자식 클래스에서 부모 클래스의 속성과 메서드를 재사용할 수 있다.
- 메서드 오버라이딩을 통해 부모의 기능을 변경하거나 확장할 수 있다.
- 다중 상속 시 메서드 탐색 순서를 이해하고 설명할 수 있다.
- super()를 사용하여 부모 클래스의 메서드를 호출할 수 있다.
- try, except, else, finally 구문을 사용하여 예외 상황을 안전하게 처리할 수 있다.

---

# 1. 상속

- 한 클래스의 속성과 메서드를 다른 클래스가 물려받는 것

## 1-1. 클래스 상속

### 상속이 필요한 이유

1. 코드 재사용
2. 클래스들 간 계층 구조 형성
3. 유지 보수의 용이성

## 1-2. 메서드 오버라이딩

- 부모 클래스의 메서드를 같은 이름, 같은 파라미터 구조로 재정의하는 것
- 자식 클래스가 부모 클래스의 메서드를 덮어써서 새로운 동작을 구현할 수 있음

## 1-3. 다중 상속

- 둘 이상의 상위 클래스로부터 여러 행동이나 특징 상속
- 중복된 속성이나 메서드가 있는 경우 상속 순서에 의해 결정(먼저 상속받은 클래스부터)
- 상속받은 모든 클래스 요소 활용 가능

## 1-4. super()

- MRO(메서드 해석 순서)에 따라, 현재 클래스의 부모 클래스의 메서드나 속성에 접근할 수 있게 해주는 내장함수

MRO가 필요한 이유

부모 클래스들이 여러 번 액세스 되지 않도록, 각 클래스에서 지정된 왼쪽에서 오른쪽으로 가는 순서를 보존하고, 각 부모를 오직 한 번만 호출하고, 부모들의 우선순위에 영향을 주지 않으면서 서브 클래스를 만드는 단조적인 구조 형성

# 2. 에러와 예외

## 2-1. 디버깅

소프트웨어에서 발생하는 버그를 찾아내고 수정하는 과정

프로그램의 오작동 원인을 식별하여 수정하는 작업

## 2-2. 에러

### 문법 에러(Syntax Error)

프로그램의 구문이 올바르지 않은 경우 발생(오타, 괄호 및 콜론 누락 등의 문법적 오류

### 예외 ⭐

프로그램 실행 중에 감지되는 에러

- 내장 예외(Built-in Exceptions): 예외 상황을 나타내는 예외 클래스들
  - ZeroDivisionError
  - NameError
  - TypeError
  - ValueError
  - IndexError
  - KeyError
  - ImportError
  - ModuleNotFoundError
  - Keyboard Interrupt
  - IndentationError

# 3. 예외 처리

- 예외 처리(Exception Handling): 예외가 발생했을 때 프로그램이 비정상적으로 종료되지 않고 적절하게 처리할 수 있도록 하는 방법
  - try: 예외가 발생할 수 있는 코드 작성
  - except: 예외가 발생했을 때 실행할 코드 작성
  - else: 예외가 발생하지 않았을 때 실행할 코드 작성
  - finally: 예외 발생 여부와 상관없이 **항상** 실행할 코드 작성

## 3-1. try-except 구조

```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print('0으로 나눌 수 없습니다.')

```

## 3-2. 복수 예외 처리

```python
try:
	num = int(intput('100으로 나눌 값을 입력하시오 : '))
	print(100/num)
except ValueError:
	print('숫자를 넣어주세요.')
except ZeroDivisionError:
	print('0으로 나눌 수 없습니다.')
except:
	print('에러가 발생하였습니다.')
```

## 3-3. else & finally

```python
try:
	x = int(input('숫자를 입력하세요:'))
	y = 10 / x
except ZeroDivisionError:
	print('0으로 나눌 수 없습니다.')
except ValueError:
	print('유효한 숫자가 아닙니다.')
else:
	print(f'결과: {y}')
finally:
	print('프로그램이 종료되었습니다.')
```
