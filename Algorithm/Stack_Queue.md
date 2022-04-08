# Stack, Queue

> 스택, 큐

## Stack

#### 특성

- 물건을 쌓아 올리듯 자료를 쌓아 올린 형태의 자료구조이다.
- 스택에 저장된 자료는 선형 구조를 갖는다.
  - 선형구조: 자료 간의 관계가 1대1의 관계를 갖는다.
  - 비선형구조: 자료 간의 관계가 1대N의 관계를 갖는다. (ex. 트리)
- 스택에 자료를 삽입하거나 스택에서 자료를 꺼낼 수 있다.
- 후입선출구조 (LIFO, Last-In-First-Out)
  - 마지막에 삽입한 자료를 가장 먼저 꺼낸다.



#### 기본 연산

- push : 저장소에 자료를 저장한다
- pop : 저장소에서 자료를 꺼낸다. 꺼낸 자료는 삽입한 자료의 역순으로 꺼낸다.
- peek : 스택의 top에 있는 원소를 반환한다.



#### Stack API

- java.util.Stack
- 주요 메소드
  - push()
  - pop()
  - peek()
  - isEmpty() 
  - size()



#### 활용

- Function call
  - 프로그램에서의 함수 호출과 복귀에 따른 수행 순서를 관리
- 계산기
  - 수식을 후위 표기식으로 변환하여 우선순위를 신경쓰지 않고 단순하게 연산 가능
- 브라우저
  - 방문한 페이지 이전, 이후 페이지를 두개의 스택으로 구현 가능



## Queue

#### 특성

- 스택과 마찬가지로 삽입과 삭제의 위치가 제한적인 자료구조
- 선입선출구조(FIFO, First-In-First-Out)



#### 기본 연산

- enQueue : 원소 삽입
- deQueue : 원소 삭제



#### Queue API

##### Java

`java.util.Queue`

- 큐에 필요한 연산을 선언해 놓은 **인터페이스**
- LinkedList 클래스를 Queue 인터페이스의 구현체(참조변수)로 많이 사용
- LinkedList는 Queue 관련 기능, Deque 관련 기능을 모두 갖고 있음

```java
Queue<String> queue = new LinkedList<String>();
// LinkedList의 기능 중 Queue에 정의된 기능만 사용할 수 있음
```

주요 메소드
- offer() : enQueue
  - queue가 꽉 차있는걸 스스로 확인한다는 점에서 add()와 다르지만 그러려면 메모리 한계까지 가야하므로 사실상 둘은 서로 다를바 없음
- poll()   : deQueue
- isEmpty()
- size()

##### Python

`from queue import Queue` [문서](https://docs.python.org/3/library/queue.html)

- `qsize()`
- `empty()`
- `full()`
- `put(item)`
- `get()`



#### 활용

- 버퍼

  - 데이터를 한 곳에서 다른 한 곳으로 전송하는 동안 일시적으로 그 데이터를 보관하는 메모리 영역

  - 일반적으로 입출력 및 네트워크 관련 기능에서 이용



#### 우선순위 큐

- 우선순위를 가진 항목들을 저장하는 큐
- 선입선출 순서가 아니라 우선순위가 높은 순서대로 먼저 나가게 된다
- java.util.PriorityQueue
  - Heap 자료구조
  - Comparator 인터페이스를 구현해 Min heap과 Max heap 구현 가능