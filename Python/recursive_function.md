# recursive function

### 재귀함수

- fibonacci 예제

```python
# 재귀
def fibo(n):
    # base case
    if n < 2:
        return n
    else:
        return fib(n-1) + fib(n-2)

# 반복
def fibo_for(n):
    if n < 2:
        return n
    
    a, b = 0, 1
    
    for i in range(n-1):
        a, b = b, a+b
    return b
```



- 재귀함수의 장점
  - 알고리즘을 재귀함수로 표현할 때 자연스러운 경우에 사용한다. (ex. 점화식)
  - 변수의 사용이 줄어들며, 코드의 가독성이 높아진다.
- 재귀함수의 단점
  - 반복문에 비해 성능이 떨어진다.
  - 메모리를 많이 사용한다.
    - 함수 호출 시 함수의 매개변수, 지역변수, 리턴 값, 그리고 함수 종료 후 돌아가는 위치가 스택 메모리에 저장된다.



### 재귀함수 디자인

재귀함수를 디자인 하기 위한 세가지 단계

1. 함수의 정의를 명확히 한다.
2. 기저 조건에서 함수가 제대로 동작하게 작성한다.
3. 함수가 작은 input에 대하여 제대로 동작한다고 가정하고 함수를 완성한다.



### 꼬리 재귀 (tail recursion)

- 컴파일러가 꼬리 재귀에 대한 최적화를 지원하는 경우, 작성한 재귀 함수를 반복문으로 변경하여 실행시킬 수 있다.

  ```C
  int Recursive(int n) 
  {
   if(n==1) return 1;
   return n + Recursive(n-1);
  }
  int Tail_Recursive(int n, int acc)
  {
   if(n==1) return acc;
   return Tail_Recursive(n-1, n + acc);
  }
  ```

  

- 파이썬은 인터프리터 언어이며, 꼬리 재귀를 지원하지 않는다.

- 하지만 꼬리 재귀가 사용된 함수를 아래와 같이 반복문으로 변경하여 사용할 수 있다.

  ```python
  def Tail_Recursive(n, acc):
      while True:
          if n == 0:
              return acc
          n, acc = n-1, acc+n
  ```

  