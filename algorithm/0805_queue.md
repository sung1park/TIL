# Queue

### 특성

- 스택과 마찬가지로 삽입과 삭제의 위치가 제한적인 자료구조
- 선입선출구조(FIFO, First-In-First-Out)



### 기본 연산

- enQueue : 원소 삽입
- deQueue : 원소 삭제



### Queue API

- java.util.Queue
  - 큐에 필요한 연산을 선언해 놓은 **인터페이스**
  - LinkedList 클래스를 Queue 인터페이스의 구현체(참조변수)로 많이 사용
  - LinkedList는 Queue 관련 기능, Deque 관련 기능을 모두 갖고 있음

```java
Queue<String> queue = new LinkedList<String>();
// LinkedList의 기능 중 Queue에 정의된 기능만 사용할 수 있음
```



- 주요 메소드
  - offer() : enQueue
    - queue가 꽉 차있는걸 스스로 확인한다는 점에서 add()와 다르지만 그러려면 메모리 한계까지 가야하므로 사실상 둘은 서로 다를바 없음
  - poll()   : deQueue
  - isEmpty()
  - size()



### 활용

- 버퍼

  - 데이터를 한 곳에서 다른 한 곳으로 전송하는 동안 일시적으로 그 데이터를 보관하는 메모리 영역

  - 일반적으로 입출력 및 네트워크 관련 기능에서 이용

    