# Data Type

>Python의 자료형과 사용법
>
>Numbers, String, Tuple, Boolean, List, Set, Dictionary



## Numbers

> int, float, complex

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

- 실수부와 허수부로 구성된 복소수



## String

- `'` 혹은 `"` 를 이용해 표기
- 소스코드 내에서는 둘 중 하나만 선택하여 이용하기 (style guide)



#### Slicing

`s[start:stop:step]`

- `s[::-1]` 문자열을 뒤집을 수 있음



#### 문자열 조회/탐색

`s.find(x)`: `x`의 첫 번째 위치를 반환. 없으면 -1을 반환

`s.index(x)`: `x`의 첫 번째 위치를 반환. 없으면 오류 발생



#### 문자열 변경

`s.replace(old, new[,count])`

- 바꿀 대상 글자를 새로운 글자로 바꿔서 변환 (복사본 반환)
- count를 지정하면, 해당 개수만큼만 시행

`s.strip([chars])`

- 특정한 문자들을 지정하면 양쪽을 제거하거나(strip), 왼쪽을 제거하거나 (lstrip), 오른쪽을 제거(rstrip)
- 문자열을 지정하지 않으면 공백을 제거함

`s.split(sep=None)`

- 문자열을 특정한 단위로 나눠 리스트로 반환

  ```
  'a,b,c'.split('-') #['a,b,c']
  'a b c'.split()    #['a', 'b', 'c']
  ```


`'<separator>'.join(iterable)`

- 반복 가능한 컨테이너 요소들을 separator(구분자)로 합쳐 문자열 반환

  ``` 
  '!'.join('sungil')   #'s!u!n!g!i!l'
  ' '.join(['3', '5']) #'3 5'
  ```


`s.capitalize()` : 앞글자를 대문자로

`s.title()` : `'`나 공백 이후를 대문자로

`s.upper()` : 모두 대문자로

`s.lower()` : 모두 소문자로

`s.swapcase()` : 대소문자 변경하여



#### 문자열 관련 검증 메서드

`s.isalpha()` : 알파벳 문자여부 (한국어도 포함)

`s.isupper()` : 대문자 여부

`s.islower()` : 소문자 여부

`s.istitle()` : 타이틀 형식 여부. 단어가 대문자로 시작하고 나머지 문자는 소문자.



## List

#### 추가 및 삭제

`l.append(x)` : 값 추가

`l.extend(iterable)` : 리스트에 iterable의 항목을 추가함. 문자열을 넣으면 문자 하나하나 추가됨

`l.insert(i, x)` : 정해진 위치`i`에 값을 추가. 리스트 길이보다 큰 경우 맨 뒤에 추가

`l.remove(x)` : 리스트에서 값이 `x`인 첫번째 항목 삭제

`l.pop(i)` : 정해진 위치 `i`에 있는 값을 삭제하고, 그 항목을 반환함.

​                   `i`가 지정되지 않으면, 마지막 항목을 삭제하고 반환함

`l.clear()` : 모든 항목을 삭제함



#### 탐색 및 정렬

`l.index(x)` : 첫번째 `x`값을 찾아 해당 index값을 반환. 없는 경우 ValueError

`l.count(x)` : 원하는 값 `x`의 개수를 반환함

`l.sort()` : 원본 리스트를 정렬함. None 반환

`l.reverse()` : 순서를 반대로 뒤집음 (정렬하는 것이 아님)



#### 리스트 복사

##### 얕은 복사 (shallow copy)

- Slice 연산자를 활용해 같은 원소를 가진 리스트의 연산된 결과를 복사 (다른 주소)

  ```python
  a = [1, 2, 3]
  b = a[:]
  ```

- list() 활용

  ```python
  a = [1, 2, 3]
  b = list(a)
  ```

- 복사하는 리스트의 원소가 주소를 참조하는 경우

  ```python
  a = [1, 2, ['a', 'b']]
  b = a[:]
  b[2][0] = 0
  # 'a'가 0으로 변경됨
  ```

  

##### 깊은 복사 (deep copy)

```python
import copy
a = [1, 2, ['a', 'b']]
b = copy.deepcopy(a)
```



#### List comprehension

- 표현식과 제어문을 통해 특정한 값을 가진 리스트를 생성하는 법

```
[<expression> for <변수> in <iterable>]
[<expression> for <변수> in <iterable> if <조건식>]
```

```python
[number ** 3 for number in range(1, 4)]
```



## Set

> 중복과 순서가 없는 자료형

#### 선언

딕셔너리와 같이 `{}`로 선언하며, 원소들에 `:`가 있는지 여부로 딕셔너리와 구분된다. `set()`을 사용해 선언할 수도 있다.

```python
set1 = {1, 2, 3}
set2 = set([1, 2, 3]) # 리스트를 집합으로
```



#### 추가 및 삭제

`s.add(elem)`: 세트에 값을 추가

`s.update(*others)`: 여러 값을 추가

`s.remove(elem)`: 세트에서 삭제하고, <u>없으면 KeyError</u>

`s.discard(elem)`: 세트에서 삭제하고, 없어도 에러가 발생하지 않음

`s.pop()`: 임의의 원소를 제거해 반환



#### 값 확인

`<el> in <set>`: 세트에 원소가 있는지 확인

`len(<set>)`: 세트의 크기 확인 



#### 연산

```python
union = set1 | set2          # 합집합
intersection = set1 & set2   # 교집합
diff = set1 - set2           # 차집합 
xor = set1 ^ set2            # XOR
```



## Dictionary

#### 딕셔너리 키

- 딕셔너리의 키는 <u>변하지 않는(immutable)</u> 값이어야 함
- `<key> in <dictionary>` 형식으로 키를 확인할 수 있음



#### 추가 및 삭제

`d.get(key[, default])`: key를 통해 value를 가져옴

- KeyError가 발생하지 않으며, default 값을 설정할 수 있음 (기본: None)

`d.pop(key[, default])`: key가 딕셔너리에 있으면 제거하고 해당 값을 반환

- 그렇지 않으면 default를 반환하고, default 값이 없으면 KeyError

`d.update(key=Value)`: 값을 제공하는 key, value로 덮어씀

- ```python
  my_dict.update(apple='사과')
  ```

`del d[key]`: key에 해당하는 항목을 삭제



#### 딕셔너리 순회

```python
for index, value in my_dict.items():
```

- 기본적으로 key를 순회하며, key를 통해 값을 활용
- `keys()`, `values()`, `items()`



#### Dictionary Comprehension

```
{key: value for <변수> in <iterable>}
{key: value for <변수> in <iterable> if <조건식>}
```

```python
dusts = {
    '서울': 72,
    '대전': 82,
    '구미': 29,
    '광주': 45,
}
result = {key: value for key, value in dusts.items() if value > 70}
```



#### JSON과 딕셔너리 변환

```python
import json
```

`json.loads()`: JSON에서 딕셔너리로 (load string)

`json.dumps()`: 딕셔너리를 JSON으로 (dump string)
