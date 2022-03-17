# function

> 파이썬의 함수, 내장함수, 람다



## 함수 Input / Output

#### 위치 인자(Positional Arguments)

- 패러미터는 위치에 따라 함수 내에 전달됨



#### 기본 인자 값(Default Arguments Values)

```python
def add(x, y=0):
```

✅ 리스트의 경우 기본 인자값을 `[]`로 설정하지 말것. `None`으로 설정하고, `None`일 경우 새로운 리스트를 만들어주는 방식으로 작성



#### 키워드 인자(Keyword Arguments)

```python
add(x=2, y=5)
```

- 직접 변수의 이름으로 특정 인자를 전달할 수 있음



#### 가변 인자 리스트(Arbitraty Argument Lists)

```python
def add(*args):
    for arg in args:
```

- 함수가 임의의 개수 인자로 호출될 수 있도록 지정
- 인자들은 튜플로 묶여 처리되며, 매개변수에 *을 붙여 표현
- `*args`는 다른 이름으로 바꿔도 되지만 관습적으로 사용함



#### 가변 키워드 인자(Arbitrary Keyword Arguments)

```python
def family(**kwargs):
    for key, value in kwargs:
```

- 함수가 임의의 개수 인자를 키워드 인자로 호출될 수 있도록 지정
- 인자들을 <u>딕셔너리</u>로 묶여 처리되며, 매개변수에 **을 붙여 표현



#### 함수 정의 주의 사항

```python
def greeting(name = 'sean don', age) # Wrong
```

- 기본 인자 값을 가지는 인자 다음에 기본 값이 없는 인자로 정의할 수 없음



#### 함수 호출 주의 사항

```python
add(x=3, 5)   # Wrong
add(*args, x) # Wrong
my_info(x, y, *args, **kwargs) # Right
```

- 키워드 인자, 가변 인자, 가변 키워드 인자가 위치 인자보다 앞쪽에 올 수 없음



#### 함수 Output

함수는 오직 한 개의 객체만 return 함

- 복수의 객체의 경우 하나의 튜플로 변환되어 return 함



## 함수 Scope

#### 변수 수명주기(lifecycle)

빌트인 스코프(built-in scope)
- 파이썬이 실행된 이후부터 영원히 유지

전역 스코프(global scope)
- 모듈이 호출된 시점 이후 혹은 인터프리터가 끝날 때까지 유지

지역(함수) 스코프(local scope)
- 함수가 호출될 때 생성되고, 함수가 종료될 때까지 유지



#### 이름 검색 규칙(Name Resolution)

- 파이썬에서 사용되는 이름(식별자)들은 이름공간(namespace)에 저장되어 있음
- LEGB Rule, 아래와 같은 순서로 이름을 찾아나감
  - Local scope
  - Enclosed scope : 특정 함수의 상위 함수
  - Global scope : 함수 밖의 모듈, Import 모듈
  - Built-in scope
- 함수 내에서는 바깥 스코프의 변수에 접근 가능하나 수정은 할 수 없음. 반대 방향은 접근도 불가.



#### global

- 현재 코드 블록 전체에 적용되며, 나열된 식별자(이름)들이 전역 변수임을 나타냄
  - global에 나열된 이름은 같은 코드 블록에서 global 앞에 등장할 수 없음
  - global에 나열된 이름은 매개변수, for 루프 대상, 클래스/함수 정의 등으로 정의되지 않아야 함
- 선언된 적 없는 변수도 활용할 수 있음
- 유지 보수에 좋지 않음



#### nonlocal

- global과 유사. 전역을 제외하고 가장 가까운 (둘러 싸고 있는) 스코프의 변수를 연결하도록 함
- global과는 달리 이미 존재하는 이름과의 연결만 가능



#### 주의

- 기본적으로 함수에서 선언된 변수는 Local scope에 생성되며, 함수 종료 시 사라짐
- 해당 스코프에 변수가 없는 경우 LEGB Rule에 의해 이름을 검색함
  - 변수에 접근은 가능하지만, 해당 변수를 수정할 수는 없음
  - 값을 할당하는 경우 해당 스코프의 이름공간에 새롭게 생성되기 때문
  - 단, 함수 내에서 필요한 상위 스코프 변수는 인자로 넘겨서 활용할 것 (클로저* 제외)
    - (참고) 클로저란 어떤 함수 내부에 중첩된 형태로써 외부 스코프 변수에 접근 가능한 함수
- 상위 스코프에 있는 변수를 수정하고 싶다면 global, nonlocal 키워드를 활용 가능
  - 단, 코드가 복잡해지면서 변수의 변경을 추적하기 어렵고, 예기치 못한 오류가 발생
  - 가급적 사용하지 않는 것을 권장하며, 함수로 값을 바꾸고자 한다면 항상 인자로 넘기고 리턴 값을 사용하는 것을 추천



## 일급 객체

파이썬의 함수는 함수를 리턴값으로 가질 수 있음



#### itemgetter

```python
from operator import itemgetter
get_zeroth = itemgetter(0)
numbers = [1, 2, 3]
print(get_zeroth(numbers))
```



#### 함수 내부에서 함수 리턴

```python
def adder(n):
    def helper(x):
        return x + n
   	return helper

add_three = adder(3)
print(add_three(6)) # 9
```





## 람다 lambda

```python
def square(x):
    return x*x

square = lambda x: x*x
```

- 간단한 함수를 한 줄로 표현 가능



#### assert

```python
assert(a == b)
```

`()`안의 조건이 맞으면 pass, 틀리면 에러를 발생시킨다



## Built-in Functions

#### map

```
map(function, iterable)
```

- 순회 가능한 데이터구조(iterable)의 모든 요소에 함수(function)를 적용하고, 그 결과를 map object로 반환 
- 리스트가 아닌 `map` 객체를 반환하며 리스트로 형변환하여 확인 가능

```python
n, m = map(int, input().split())
```



####  filter

```
filter(function, iterable)
```

- 순회 가능한 데이터구조(iterable)의 모든 요소에 함수(function)를 적용하고, 그 결과가 True인 것들을 filter object로 반환
- 리스트가 아닌 `filter` 객체를 반환하며 리스트로 형변환하여 확인 가능



#### zip

```
zip(*iterables)
```

- 복수의 iterable을 모아 튜플을 원소로 하는 zip object를 반환

```python
girls = ['jane', 'ashley']
boys = ['justin', 'eric']
pair = zip(girls, boys)
[('jane', 'justin'), ('ashley', 'eric')]
```





