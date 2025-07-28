# [0728] Python 5일차 - Data Structure

Table of Contents

1. 데이터 구조
2. 시퀀스 데이터 구조

   2-1. 문자열

   2-2. 리스트

3. 복사

   3-1. 객체와 참조

   3-2. 얕은 복사

   3-3. 깊은 복사

Objectives

- 데이터 구조의 개념과 필요성을 이해하고 설명할 수 있습니다.

- 문자열(String)의 다양한 메서드를 활용하여 텍스트 데이터를 처리할 수 있습니다.

- 리스트(List)의 주요 메서드를 사용하여 데이터를 추가, 삭제, 탐색, 정렬할 수 있습니다.

- 객체, 참조, 가변성의 개념을 이해하고 파이썬 변수 할당의 원리를 설명할 수 있습니다.

- 얕은 복사와 깊은 복사의 차이를 이해하고 적절하게 활용할 수 있습니다.

- List Comprehension을 사용하여 간결하고 효율적인 리스트 생성을 할 수 있습니다.

- 메서드 체이닝의 원리를 이해하고 코드를 더 효율적으로 작성할 수 있습니다.

---

# 1. 데이터 구조

여러 데이터를 효과적으로 사용하고 관리하기 위한 구조

str, list, dict 등

## 메서드?

- 객체에 속한 함수: 프로그래밍에서 메서드는 객체가 특정 작업을 수행하도록 정의된 함수
- 문자열, 리스트, 딕셔너리 등 각 데이터 구조의 메서드를 호출하여 다양한 기능을 활용하기
- 메서드는 어딘가(클래스)에 속해 있는 함수이며, 각 데이터 타입별로 다양한 기능을 가진 메서드가 존재

<호출 방법>

데이터 타입 객체.메서드()

→ 우리가 만든 객체에게 원하는 명령(메서드)을 내리는 방법

# 2. 시퀀스 구조

## 2-1. 문자열 str

**불변 객체라 원본을 바꾸는 게 아니라 새롭게 할당하는 것**

- s. find(x) → x의 첫 번째 위치를 반환, 없으면 -1을 반환
- s.index(x) → x의 첫 번째 위치를 반환, 없으면 오류 발생
- s.isupper() → 문자열 내의 모든 문자가 대문자인지 확인
- s.islower() → 문자열 내의 모든 문자가 소문자인지 확인
- s.isalpha() → 문자열이 알파벳으로만 이루어져 있는지 확인

- s.replace(old, new[,count]) → 바꿀 대상 글자를 새로운 글자로 바꿔서 반환
- s.strip([chars]) → 문자열의 시작과 끝에 있는 공백 혹은 지정한 문자를 제거
- s.split(sep=None, maxsplit=-1) → sep 구분자 문자열로 사용하여 문자열에 있는 단어들의 **리스트**를 반환 😀
  - seperate 값이 없으면 공백을 기준으로 자름
- ‘seperator’.join(iterable) → iterable 의 문자열을 연결한 문자열을 반환 😀

```python
# 추가!

# capitalize
text = 'heLLo, woRld!'
new_text1 = text.capitalize()
print(new_text1)  # Hello, world!

# title
new_text2 = text.title()
print(new_text2)  # Hello, World!

# upper
new_text3 = text.upper()
print(new_text3)  # HELLO, WORLD!

# lower
new_text4 = text.lower()
print(new_text4)  # hello, world!

# swapcase
new_text5 = text.swapcase()
print(new_text5)  # HEllO, WOrLD!

```

## 2-2. 리스트

문자열과 달리 가변객체라 원본을 조작한다. **따라서, 반환값이 없다!**

- L.append(x) → 리스트 마지막에 항목 x를 추가
- L.extend(m) → Iterable m의 모든 항목들을 리스트 끝에 추가(+=과 같은 기능)
  - extend vs append
  - 반복 가능한 객체가 아니면 추가 불가
- L.insert(i, x) → 리스트 인덱스 i에 항목 x를 삽입

- L.remove(x) → 리스트에서 첫 번째로 일치하는 항목을 삭제
- L.pop() → 리스트에서 지정한 인덱스의 항목을 제거하고 반환, 작성하지 않을 경우 마지막 항목 제거
- L.pop(i) → 리스트의 인덱스 i에 있는 항목을 반환 후 제거
- L.clear() → 리스트의 모든 항목을 삭제

### 리스트 탐색 및 정렬 메서드

- L.index(x) → 리스트에서 첫 번재로 일치하는 항목 x의 인덱스를 반환
- L.count(x) → 리스트에서 항목 x의 개수를 반환
- 🍅L.reverse() → 리스트의 순서를 역순으로 변경 (정렬 XXXX)
- 🍅L.sort → 원본 리스트를 오름차순으로 정렬
  - my_list.sort(reverse=True) 은 내림차순 정렬!

# 3. 복사

객체 복사의 핵심을 파악하려면, 파이썬 자료구조의 가변과 불변 두 가지 종류를 살펴봐야 한다.

**가변 Mutable**

- 생성 뒤 내용을 변경할 수 있는 객체: **리스트, 딕셔너리, 집합**
- 객체의 내용이 변경되어도 같은 메모리 주소 유지
- 내용 수정이 빈번할 때, 새로운 객체를 생성하는 대신 기존 객체를 직접 수정할 수 있음. 이로 인해 객체 생성 및 삭제에 드는 비용을 절감하여 성능을 향상시킴
- 크기가 큰 데이터를 효율적으로 수정 가능

```python
a = [1, 2, 3, 4]
b = a
b[0] = 100

print(a) # [100, 2, 3, 4]
print(b) # [100, 2, 3, 4]
print(a is b) # True
```

**불변 Immutable**

- 생성 뒤 내용을 변경할 수 없는 객체: **정수, 실수, 문자열, 튜플**
- 새로운 값을 할당하면 새로운 객체가 생성되고, 변수는 새 객체를 참조
- 변경이 불가능하므로 여러 변수가 동일한 객체를 안전하게 공유할 수 있음
- 동일한 값을 가진 여러 변수가 같은 객체를 참조할 수 있어 메모리 사용 최적화

```python
a = 20
b = a
b = 10

print(a) # 20
print(b) # 10
print(a is b) # False
```

## 3-1. 얕은 복사

객체의 최상위 요소만 새로운 메모리에 복사하는 방법. 내부에 중첩된 객체가 있다면 그 객체의 참조만 복사됨. 얕은 복사 후 중첩된 리스트나 딕셔너리 같은 가변 객체를 수정하면, 원본 객체와 복사본 객체가 함께 변경됨.

### 구현방법

리스트 슬라이싱

copy() 메서드

list 함수

1차원 리스트: 얕은 복사로 충분히 독립적인 복사본 만들 수 있음

다차원 리스트: 최상위 리스트만 복사되고, 내부 리스트는 여전히 원본과 같은 객체를 참조함

```python
a = [1, 2, [3, 4, 5]]
b = a[:]

b[0] = 999
print(a) # [1, 2, [3, 4, 5]]
print(b) # [999, 2, [3, 4, 5]]

b[2][1] = 100
print(a) # [1, 2, [3, 100, 5]]
print(b) # [999, 2, [3, 100, 5]]

print(f'a[2]와 b[2]가 같은 객체인가? {a[2] is b[2]}') # True
```

## 3-2. 깊은 복사

객체의 모든 수준 요소를 새로운 메모리에 복사하는 방법. 중첩된 객체까지 모두 새로운 객체로 생성됨.

원본 객체와 복사본은 완전히 독립적이며, 복사본을 수정하더라도 원본은 절대 바뀌지 않음.

### 구현방법

copy 모듈에서 제공하는 deepcopy() 함수를 사용

```python
import copy

a = [1, 2, [3, 4, 5]]
b = copy.deepcopy(a)

b[2][1] = 100

print(a) # [1, 2, [3, 4, 5]]
print(b) # [1, 2, [100, 4, 5]]
print(f'a[2]와 b[2]가 같은 객체인가? {a[2] is b[2]}') # False
```

# 4. 참조

### List Comprehension

“Pythonic”한 코드, 간결하고 효율적인 **리스트 생성** 방법

- 2차원 배열 생성 시 많이 사용 (인접행렬 생성)
- Simple is better than complex. Keep it simple, stupid.

```python
numbers = [1, 2, 3, 4, 5]
squared_numbers = [num**2 for num in numbers]
squared_numbers = list(num**2 for num in numbers)
```

### 메서드 체이닝

여러 메서드를 연속해서 호출하는 방식

```python
numbers = [3, 1, 4, 1, 5, 9, 2]
result = numbers.copy().sort()
print(numbers) # [3, 1, 4, 1, 5, 9, 2]
print(result) # None (sort() 메서드는 Noned을 반환하기 때문!)

#올바른 체이닝 예시
sorted_numbers = sorted(numbers.copy())
print(sorted_numbers) # [1, 1, 2, 3, 4, 5, 9]
```
