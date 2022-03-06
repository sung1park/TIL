# NumPy 사용해보기

> NumPy, Indexing/Slicing, numpy 연산, 집계함수&마스킹연산



## NumPy?

> Python에서 대규모 다차원 배열을 다룰 수 있게 도와주는 라이브러리

### Why? 

데이터의 대부분은 숫자 배열로 볼 수 있다.

C++ 기반으로 만들어진 라이브러리. 연산이 빠르다.



## NumPy 배열

### 배열 만들기

- numpy 배열은 자료형이 하나로 통일 되어야 함
  - 연산을 빠르게 하기 위해

```python
np.array([1, 2, 3, 4, 5])
# array([1, 2, 3, 4, 5])
np.array([3, 1.4, 2, 3, 4])
# array([3. , 1.4, 2. , 3. , 4. ])
np.array([[1, 2],
          [3, 4]])
# array([[1, 2],
#        [3, 4]]), 2차원 배열
np.array([1, 2, 3, 4], dtype='float')
# array([1. , 2. , 3. , 4. ]), 가장 좋은 방법
```



### 배열 데이터 타입

##### dtype

- 데이터 타입을 지정 혹은 확인 (d-type) 
- int, float, str

##### astype

- 데이터 타입 변경



### 다양한 배열 만들기

##### zeros

- 0으로 채우기
- `np.zeros(10, dtype=int)`

##### ones

- 1로 채우기
- `np.ones((3, 5), dtype=float)`

##### arange

- python의 range 함수 역할
- `np.arange(0, 20, 2)`

##### linspace

- 범위 지정, 일정한 간격으로 배열 생성
- `np.linspace(0, 1, 5)`



### 난수로 채워진 배열 만들기 (random)

##### random

- `np.random.random((2, 2))`

##### normal

- 정규 분포를 따르는 값

- `np.random.normal(0, 1, (2, 2))`

##### randint

- 랜덤 정수 

- `np.random.randint(0, 10, (2, 2))`

- `np.random.randint(5, size=(3, 5))`



### 배열 기초

- ndim : n-dim 차원

- shape : 행, 열

- size : 원소의 개수

- dtype : 타입



### 모양 바꾸기

##### reshape

- array의 shape를 변경
- `-1`을 넣을 수 있음
- `x.reshape((2, 4))`



### 이어 붙이기/나누기

##### concatenate

- axis 축을 기준으로 이어 붙임
- axis는 [0, 1, 2, 3, ...] 으로 이해하면 쉬움
- `np.concatenate([x, y], axis=0)`

##### split

- axis 축을 기준으로 분할
- `upper, lower = np.split(matrix, [3], axis=0)`



### 찾고 잘라내기 Indexing / Slicing

##### Indexing 

- (정수) 인덱스로 값을 찾아냄

##### Slicing

- 인덱스 값으로 배열의 부분을 가져옴
- `x[start: end: step]`
- 이차원배열 `x[start1: end1, start2: end2]`



## NumPy 연산

### 기본 연산

- array는 `+`, `-`, `*`, `/`에 대한 기본 연산을 지원

- 크기가 큰 배열에 대해 루프는 느리기 때문에 numpy 배열을 사용하면 용이

- 다차원 행렬 간에도 적용 가능



### 브로드캐스팅 Broadcasting

- shape이 다른 array끼리 연산
- 예를 들어, 3x3 행렬과 1x3 행렬을 더하는 경우 1x3 행렬을 3x3 사이즈로 복사해 더함



### 집계함수

- `np.sum(array, axis=0)` 처럼 축을 지정할 수 있음
- `matrix.sum(axis=0)` 처럼 python 자체의 메서드를 사용할 수 있음

##### sum

##### min

##### max

##### mean



### 마스킹 연산

Boolean(True, False) array를 통해서 특정 값들을 뽑아내는 방법

```python
x = np.arange(5) 
# array([0, 1, 2, 3, 4])
x < 3
# array([True, True, True, False, False])
x > 5
# array([False, False, False, False, False])
x[x < 3]
# array([0, 1, 2])
```

