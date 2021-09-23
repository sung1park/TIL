# Heap, Priority Queue

> Heap 자료구조와 Heap 구현에 자주 사용되는 Priority Queue



## Heap

> Complete binary tree의 노드 중 키 값이 가장 큰 노드나 가장 작은 노드를 찾기 위해 사용하는 자료구조

- 노드 하나를 삽입, 삭제, 탐색할 때 시간 복잡도가 작아 최대값, 최소값을 활용해야 할 때 유용하게 사용 가능

  - 삽입 : O(logN), O(NlogN) (N개를 삽입할 때)
  - 삭제 : O(logN), O(NlogN) (N개를 삭제할 때)
  - 최대/최소 탐색 : O(1)

  

#### Max heap

- 키 값이 가장 큰 노드를 찾기 위한 complete binary tree
- 부모 노드의 키 값 > 자식 노드의 키 값
- 루트 노드 : 키 값이 가장 큰 노드 



#### Min heap

- 키 값이 가장 작은 노드를 찾기 위한 complete binary tree
- 부모 노드의 키 값 < 자식 노드의 키 값
- 루트 노드 : 키 값이 가장 큰 노드



#### 삽입

1. Complete binary tree의 가장 끝 노드에 새로운 키 삽입
2. 부모 노드와 비교하며 부모 노드보다 작으면(크면) 자리 바꾸기
3. 자리가 확정될 때 까지 반복



#### 삭제

- 루트 노드의 원소만을 삭제할 수 있음

1. 루트 노드의 원소값 삭제, 반환
2. 마지막 노드를 루트 노드로 가져옴
3. 자식 노드 중 더 작은(큰) 값과 비교하며 자리 바꾸기
4. 자리가 확정될 때 까지 반복



## Priority Queue

> 우선순위 큐를 구현하는 가장 효율적인 방법

- Complete binary tree 구조이기 때문에 배열을 이용해 구현하는 것이 효율적

- n위치에 있는 노드의 자식은 2n, 2n+1 위치에 존재 (heap은 일반적으로 루트 번호가 1)

- java.util.PriorityQueue

  - 원소들의 natural ordering에 따라 heap을 유지
  - Comparable 인터페이스를 구현함으로써 기준을 세울 수 있음

  