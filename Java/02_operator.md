# operators

> Java의 연산자



### 정수의 연산

- 이항 연산에서 최소 연산 타입은 `int`이다
  - 따라서 `byte`+`byte`는 `int`
  - 단항 연산자(`++`, `--`)의 경우 형변환이 일어나지 않음

- 오버플로우는 논리적 오류

```java
int i1 = Integer.MAX_VALUE;
int i2 = i1 + 1;
System.out.println(i2) // -2147483648
```



### 실수의 연산

- `float`, `double`은 실수값의 근사값을 표현하기 때문에 정확하지 않음
- `BigDecimal` 클래스를 이용해 정확한 값을 구할 수 있음



### shift 연산자

- `*2`, `/2`에 비해 속도가 빠름

- `<<`
- `>>` 
  - MSB에 부호에 맞는 숫자를 채워넣음
- `>>>`
  - 부호 bit를 신경쓰지 않고 MSB에 0을 채워넣음



### 논리 연산자

- short circuit 연산자
  - `&&`
  - `||`



### 삼항 연산자

- `<condition>?<if true>:<if false>`



### switch~case

- `switch()`에는 `double`, `String`, `enum`은 사용할 수 없음
  - JDK 1.8 이상부터는 `String` 사용 가능 



