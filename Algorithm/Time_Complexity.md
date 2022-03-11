# 시간 복잡도

> Time Complexity. Big-Oh Notation으로 표기

- 큰 데이터를 다루는 프로그램일수록 알고리즘의 시간 복잡도를 계산하고 고려하는 과정이 중요하다.

- 시간 복잡도를 측정하는 하드웨어가 다르거나 Input 데이터가 달라지면 러닝 타임도 그에 따라 다르게 측정된다. 따라서, 실험적으로 측정하는 방법에는 한계가 있으므로 <u>이론적인 방법</u>으로 시간 복잡도를 측정한다.



### Primitive Operations

- 알고리즘에 의해 수행되는 기본 연산 과정이다
- 하나의 연산 과정이 1 단위 시간을 소모한다고 가정한다
- 예를 들면, 표현식을 계산하거나, 변수에 값을 저장하거나, 배열에 접근하거나, 메서드를 호출하거나, 메서드로부터 반환값을 받는다거나 하는 과정을 말한다.



### Seven Important Functions

![image-20220311154005789](C:\Users\sungi\TIL\Algorithm\assets\image-20220311154005789.png)

- 아래로 내려올 수록 n값의 증가에 따라 함수값이 더 빠르게 증가한다



### Big-Oh Notation

```
주어진 함수 f(n), g(n)에 대해,
f(n) <= c*g(n) for n >= n0 를 만족하는 양수 c, n0가 존재한다면
f(n)은 O(g(n)) 이라고 한다.
```

예를 들어, `2n+10`이 `O(n)`임을 증명하는 과정은 아래와 같다.

```
2n + 10 <= cn
(c-2)n >= 10
n >= 10/(c-2) 이므로 c=3, n0=10이 존재한다.
```

##### 규칙

- 낮은 차수의 항은 지운다. 상수항은 지운다.
- `O( )`안에는 가능한 가장 작은 표현을 적는다.
- `O( )`안에는 가능한 가장 간단한 표현을 적는다.



### Asypmtotic Algorithm Analysis

```
Asymptotic worst-case running time
= Number of primitive operations on worst-case input with size n
  when n tends to infinity
```

- n이 매우 크다고 가정하고 시간 복잡도를 계산한다

1. 알고리즘의 <u>worst case</u>에서의 primitive operation을 세고 input size `n`에 대해서 표현한다.
2. 알고리즘을 Big-Oh notation으로 표현한다. 

➡"알고리즘이 O(n) 시간으로 동작한다."