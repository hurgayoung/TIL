# [0723] Python 3일차 - 함수

### Table of contents
1. 함수
2. 매개변수와 인자
3. 내장 함수
4. 함수와 scope
5. 함수 스타일 가이드
6. packing & unpacking


### Objectives
- 함수의 기본 구조를 이해하고, 직접 함수를 정의할 수 있다.
- 다양한 인자 전달 방식을 목적에 맞게 활용할 수 있다.
- 재귀 함수의 개념과 동작 원리를 이해하고, 간단한 문제를 재귀적으로 해결할 수 있다.
- 다양한 내장 함수(len, max, sun)을 활용할 수 있다.
- 지역/전역 변수의 개념과 변수의 유효 범위(Scope)를 설명할 수 있다.
- 함수 이름 규칙과 단일 책임 원칙을 준수하여 가독성 좋은 함수를 작성할 수 있다.
- 패킹/언패킹을 통해 가변 인자를 다룰 수 있다.



## 1. 함수

## 1-1. 함수란

특정 작업을 수행하기 위한 **재사용** 가능한 코드 묶음

함수를 사용하는  이유

- 함수를 정의하고 사용함으로써 코드의 중복을 방지
- 재사용성이 높아지고, 코드의 **가독성**과 **유지보수성** 향상

함수 호출 (function call)

- 함수를 실행하기 위해 함수의 이름을 사용하여 해당 함수의 코드 블록을 실행하는 것
- 표기법 function_name(arguments)

## 1-2. 함수의 구조


Docstring 설명서 (선택사항)

function body **들여쓰기** 필수

return value 반환 값

## 1-3. 함수 정의와 호출

- 함수의 정의
    - 함수 정의는 def 키워드로 시작
    - def 키워드  이후 함수 이름 작성
    - 괄호 안에 매개변수를 정의할 수 있음
    - 매개변수(parameter)는 함수에 전달되는 값

- 함수 body
    - 콜론(:) 다음에 들여쓰기 된 코드 블록
    - 함수가 실행될 때 수행되는 코드 정의

- Docstring
    - 함수 body 앞에 선택적으로 작성 가능한 함수 설명서
    
- 함수 반환 값
    - 함수는 필요한 경우 결과를 반환할 수 있음
    - return 키워드 이후에 반환할 값을 명시
    - return 문은 함수의 실행을 종료하고, 결과를 호출 부분으로 반환
    - 함수 내에 return 문이 없다면 None이 반환됨
        - 작성자가 return 작성 안 하면 → return None

- 함수 호출
    - 함수를 사용하기 위해서는 호출이 필요
    - 함수의 이름과 소괄호를 활용해 호출
    - 필요한 인자를 전달해야 함
    - 호출 부분에서 전달된 인자는 함수 정의 시 작성한 매개변수에 대입됨

print() 함수는 반환  값이 없음!

- print() 함수는 화면에 값을 출력하기만 할 뿐, 반환 값(return)이 없음
- 반환(코드가 등장) vs 출력(개발자에게 까만 창에서 화면 보여주기)
- 파이썬에서 반환 값이 없는 함수는 기본적으로 None을 반환한다고 간주함

# 2. 매개변수와 인자

## 2-1. 정의

매개변수(parameter): 함수를 정의할 때, 함수가 받을 값을 나타내는 변수

인자(argument): 함수를 호출할 때, 실제로 전달되는 값

```python
def add_numbers(x, y):  # x와 y는 매개변수
    result = x + y
    return result


a = 2
b = 3

sum_result = add_numbers(a, b)  # a와 b는 인자
print(sum_result)  # 5
```


## 2-2. 다양한 인자 종류

### (1) Positional Arguments 위치 인자

- 함수 호출  시 **인자의 위치에 따라 전달**되는 인자
- *위치 인자는 함수 호출 시 반드시 값을 전달해야 함*

### (2) Default Argument Values 기본 인자 값

- 함수 정의에서 **매개변수에 기본 값을 할당**하는 것
- *함수 호출 시 인자를 전달하지  않으면, 기본값이 매개변수에 할당됨*

### (3) Keyword Arguments 키워드  인자

- 함수 호출 시 **인자의 이름과 함께 값을 전달**하는 인자
- 매개변수와 인자를 일치시키지 않고, 특정 매개변수에 값을 할당할 수 있음
- 인자의 순서는 중요하지 않으며, 인자의 이름을 명시하여 전달
- *단, 호출 시 키워드 인자는 위치 인자 뒤에 위치해야 함*

### (4) Arbitary Argument Lists

- **정해지지 않은 개수의 인자를 처리**하는 인자
- 함수 정의 시 매개변수 앞에 *를여 사용
- *여러 개의 인자를 tuple로 처리*

### (5) Arbitary Keyword Argument Lists

- **정해지지 않은 개수의 키워드 인자를 처리**하는 인자
- 함수 정의 시 매개변수 앞에 **‘**’**를 붙여 사용
- *여러 개의 인자를 dictionary로 묶어 처리*

```python
# 1. Positional Arguments : 이름 없이 넣은 것
def greet(name, age):
    print(f'안녕하세요, {name}님! {age}살이시군요.')


greet('Alice', 25)  # 안녕하세요, Alice님! 25살이시군요.
greet(25, 'Alice')  # 안녕하세요, 25님! Alice살이시군요.
greet('Alice')  # TypeError: greet() missing 1 required positional argument: 'age'


##########################################


# 2. Default Argument Values
def greet(name, age=20):
    print(f'안녕하세요, {name}님! {age}살이시군요.')


greet('Bob')  # 안녕하세요, Bob님! 30살이시군요.
greet('Charlie', 40)  # 안녕하세요, Charlie님! 40살이시군요.


##########################################


# 3. Keyword Arguments
def greet(name, age):
    print(f'안녕하세요, {name}님! {age}살이시군요.')


greet(name='Dave', age=35)  # 안녕하세요, Dave님! 35살이시군요.
greet(age=35, name='Dave')  # 안녕하세요, Dave님! 35살이시군요.
greet(age=35, 'Dave')  # Positional argument cannot appear after keyword arguments


##########################################


# 4. Arbitrary Argument Lists
def calculate_sum(*args):
    print(args)  # (1, 100, 5000, 30)
    print(type(args))  # <class 'tuple'>


calculate_sum(1, 100, 5000, 30)


##########################################


# 5. Arbitrary Keyword Argument Lists
def print_info(**kwargs):
    print(kwargs)


print_info(name='Eve', age=30)  # {'name': 'Eve', 'age': 30


##########################################


# 인자의 모든 종류를 적용한 예시
def func(pos1, pos2, default_arg='default', *args, **kwargs):
    print('pos1:', pos1)
    print('pos2:', pos2)
    print('default_arg:', default_arg)
    print('args:', args)
    print('kwargs:', kwargs)


func(1, 2, 3, 4, 5, 6, key1='value1', key2='value2')
"""
pos1: 1
pos2: 2
default_arg: 3
args: (4, 5, 6)
kwargs: {'key1': 'value1', 'key2': 'value2'}
"""

```



## 2-3. 함수 인자 권장 작성 순서

- 위치 → 기본 → 가변  → 가변 키워드

# 3. 재귀 함수

## 3-1. 재귀 함수

- 함수 내부에서 자기 자신을 호출하는 함수
- 특징
    - 대표 예시는 팩토리얼 (n!)
    - 큰 문제를 작게 쪼개서 해결하는 문제에 사용
    - 특정 알고리즘 식을 표현할 때 변수의 사용이 줄어들며, 코드의 가독성이 높아짐
    - **1개 이상의 base case**(종료되는 상황)가 존재하고, **수렴**하도록 작성
    - **종료 조건**을 명확히 할 것
    - 반복되는 호출이 종료 조건을 향하도록 할 것

# 4. 내장 함수 (Built-in function)

- 파이썬이 기본적으로 제공하는 함수
- 별도의 import 없이 바로 사용 가능!
- 대표적으로 print 가 있다

```python
# 자주 쓰이는 내장 함수 예시

numbers = [1, 2, 3, 4, 5]

print(numbers) # [1, 2, 3, 4, 5]
print(len(numbers)) # 5
print(max(numbers)) # 5
print(min(numbers)) # 1
print(sum(numbers)) # 15
print(sorted(numbers, reverse=True)) # [5, 4, 3, 2, 1]
```

# 5. 함수의 Scope

## 5-1. Scope

- 파이썬의 범위
    - 함수는 코드 내부에 local scope를 생성하며, 그 외의 공간인 global scope로 구분
- 범위와 변수의 관계
    - scope
        - global scope : 코드 어디에서든 참조할 수 있는 공간
        - local scope : 함수 내부에서만 참조 가능한 함수가 만든 scope
    - variable
        - global variable
        - local variable

- 변수 수명주기: 변수가 선언되는 위치와 scope에 따라 결정됨
    - built-in scope
    - global scope : 모듈이 호출되 시점 혹은 인터프리터가 끝날 때까지 유지
    - local scope : 함수가 호출될 때 생성, 함수가 종료될 때까지 유지

## 5-2. 이름 검색 규칙

- LEGB Rule 퀴즈 ⭐
- 파이썬에서 사용되는 이름(식별자)들은 특정한 이름공간에 저장되어 있음
- 함수 내에서는 바깥 Scope의 변수에 접근 가능하나 수정할 수 없음

## 5-3. global 키워드

- 변수의 스코프를 전역 범위로 지정하기 위해 사용
- 일반적으로 함수 내에서 전역 변수를 수정하려는 경우에 사용

```python
num = 0  # 전역 변수

def increment():
		global num # num을 전역 변수로 선언
		num += 1
		
print(num)  # 0
increment()
print(num)  # 1
```

# 6. 함수 스타일 가이드

## 6-1. 함수 이름 작성 규칙

- 소문자와 언더스코어(_) 사용
- 동사로 시작하여 함수의 동작 설명
- 약어 사용 지양

이름 구성 요소

- 동사 + 명사
    - save_user()
- 동사 + 형용사 + 명사
    - calculate_total_price()
- get / set 접두사
    - get_username(), set_username()
- 리턴값 T/F 인 경우
    - is_

## 6-2. 단일 책임 원칙

- 모든 객체는 하나의 명확한 목적과 책임만을 가져야 함\
- 함수 설계 원칙
1. 명확한 목적
    1. 함수는 한 가지 작업만 수행
    2. 함수 이름으로  목적을 명확히 표현
2. 책임 분리
    1. 데이터 검증 처리, 저장 등을 별도 함수로 분리
    2. 각 함수는 독립적으로 동작 가능하도록 설계
3. 유지보수성
    1. 작은 단위의 함수로 나누어 관리
    2. 코드 수정 시 영향 범위를  최소화

# 7. Packing & Unpacking

## 7-1. Packing

여러 개의 데이터를 하나의 컬렉션으로 모아 담는 과정

- 여러 개의 값을 하나의 튜플로 묶는 파이썬의 기본 동작
- 한 변수에 콤마로 구분된 값을 넣으면 자동으로 튜플로 처리

‘*’을 활용한 패킹 (함수 매개변수 작성 시)

- 남는 위치 인자들을 튜플로 묶기
- *를 붙인 매개변수가 남는 위치 인자들을 모두 모아 하나의 튜플로 만듦

‘**’을 활용한 패킹 (함수 매개변수 작성 시)

- 남는 위치 인자들을 딕셔너리로 묶기
- **를 붙인 매개변수가 남는 키워드 인자들을 모두 모아 하나의 딕셔너리로 만듦

## 7-2. Unpacking

컬렉션에 담겨있는 데이터들을 개별 요소로 펼쳐 놓는 과정

- 튜플이나 리스트 등의 객체의 요소들을 개별 변수에 할당
- ‘시퀀스 언패킹 ’ 또는 ‘다중 할당’이라고 부름

‘*’을 활용한 언패킹 (함수 인자 전달)

- 리스트나 튜플 앞에 *를 붙여 각 요소를 함수의 개별 위치 인자로 전달

**’을 활용한 언패킹 (함수 매개변수 작성 시)

- 딕셔너리 앞에 **를 붙여 {키:값} 쌍을 키=값 형태의 키워드 인자로 전달


# 8. 참고

## 8-1. 함수의 반환

함수의 return, 반환의 원칙

- 파이썬 함수는 언제나 단 하나의 값(객체)만 반환 가능함
- 여러 값을 변환하는 경우에도 하나의 튜플로 패킹하여 반환
- 반환된 튜플은 각 변수에 언패킹하여 사용할 수 있음

## 8-2. 람다 표현식

- 익명 함수를 만드는 데 사용되는 표현식
- 간단한 연산이나 함수를 한 줄로 표현할 때 사용
- 한 줄로 간단한 함수를 정의