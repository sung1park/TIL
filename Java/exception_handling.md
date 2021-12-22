# exception handling

> 예외처리



### Error 

- compile error : 문법적 오류
- 논리 error 
- system error



### Exception

- runtime exception 
  - RuntimeException을 상속받은 exception
  - 코드 상 예외처리 하지 않음. Logic으로 처리
- non-runtime exception
  - RuntimeException을 상속받지 않은  exception
  - 반드시 코드 상에서 예외처리 해야함



### 예외 처리

##### throws

- 문제가 생길 경우 호출한 곳으로 exception을 던짐 



##### try ~ catch ~ finally

- `try` : 일단 호출해 봄

- `catch` : exception이 날아오면 대처하는 code를 작성

- 다중 catch 시 상위 exception이 하위 exception보다 먼저 catch 불가능

- 선언된 method에서 처리하면 한가지 방법으로, 

  throws 후 선언하는 method에서 처리하면 각각의 방법으로 만들 수 있음

