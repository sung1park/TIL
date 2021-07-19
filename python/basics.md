# Python 기본 문법

#### 스타일 가이드

- https://www.python.org/dev/peps/pep-0008/



#### 주석

- 기본적으로 `#`으로 표현
- `'''`, `"""`로도 사용 가능하지만 주로 docstring 작성에 이용

- `ctrl`+`/`로도 가능



#### 변수

- type() : 변수 타입 확인, id() : 변수 메모리 주소 확인

- 여러 변수에 값을 할당하는 방법은 아래와 같음

  ```python
  x = y = 1004
  x, y = 1, 2
  ```

- 두 값을 swap하기 위해 아래와 같은 방법을 사용할 수 있음 (Pythonic)

  ```python
  x, y = 10, 20
  y, x = x, y
  ```

- 예약어, 내장함수, 모듈 등의 이름으로 변수명을 정하면 안됨



#### 데이터 타입

- int, float, complex, string, boolean

`int`

- 모든 정수는 그 사이즈에 상관없이 `int`
- 수의 크기에 따라 가용적으로 메모리를 할당

`float`

- 정수가 아닌 모든 실수는 `float`
- Floating point rounding error
- 3.14 - 3.02 = 0.1200000000000001
- 무한한 실수 중에서 가장 근사한 값을 표시
- 실수를 비교할때는 두 값의 차이를 이용
- import math / math.isclose(a, b) 혹은 import sys / epsilon 이용

`complex`

- 실수부와 허수부로 구성된 복소수는 `complex`

`str`

- `'` 혹은 `"` 를 이용해 표기
- 소스코드 내에서는 둘 중 하나만 선택하여 이용하기 (style guide)



#### 타입 변환

1. Implicit type conversion
   - 암시적 형변환
2. Explicit type conversion
   - 명시적 형변환

- str => int, float / int, float, tuple, dict, ... => str
- 문자열은 암시적 형변환이 되지 않음



#### 연산자

- quotient, remainder = divmod(5, 2)
- 변수가 비어있는지 확인하기 위해서는 `x == None`이 아닌 `x is None`을 이용해야 함

- 논리 연산자는 단축평가를 함; 결과가 확실한 경우 두번째 값은 확인하지 않음

  - ```python
    a = 5 and 4
    print (a)
    4
    ```

  - ```python
    b = 5 or 3
    print (b)
    5
    ```
  - ```python
    c = 0 and 5
    print (c)
    0
    ```
  - ```python
    d = 5 or 0
    print (d)
    5
    ```

- Concatenation

  - `+` 를 이용해 표현, 다양한 데이터 타입에서 사용 가능

- Containment Test

  - ```python
    'a' in 'apple'
    ```

- Identity

  - `is`를 통해 동일한 객체인지 확인 가능
  - 파이썬에서는 `-5`~`256`까지의 숫자의 id는 동일

- Indexing / Slicing
  - `str[start:stop:step]`



#### 컨테이너

- tuple

  - List와 유사하지만 수정 불가능함 (immutable)

  - `()` 또는 `tuple()`로 생성

  - 시퀀스형 컨테이너이므로 인덱스로 접근 가능

  - 일반적으로 파이썬 내부에서 사용됨

    ```python
    # 아래는 tuple (1, 2)로 처리됨
    x, y = 1, 2
    # 아래는 'tuple' 출력
    print(type(divmod(5, 2)))
    ```

  - 하나의 항목으로 구성된 튜플은 생성시 값 뒤에 쉼표를 붙여야 함 ex) `(1, )`

- range

  - `range(start, stop, step)`

- slicing 은 각각의 인덱스 사이사이에 숫자를 붙여 생각하면 쉬움 

- 문자열에서 최대 최소는 ASCII 코드를 따름

- immutable 타입의 객체를 변수에 저장하면 call by value
  mutable 타입의 객체를 변수에 저장하면  call by reference



#### 제어문

- 조건 표현식

  ```python
  value = num if num >= 0 else -num
  ```



#### 반복문

- enumerate

  - (index, value) 형태의 tuple로 구성된 열거 객체를 반환

  ```python
  for idx, member in enumerate(members):
      print(idx, member)
  ```

  

