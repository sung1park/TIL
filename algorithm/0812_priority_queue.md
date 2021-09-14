# priority queue



- 우선순위 큐를 구현하는 가장 효율적인 방법이 힙을 사용하는 것
  - 추가 삭제 O(logN), 최대/최소값은 O(1)에 구할 수 있음



- 우선순위 큐의 특성
  - 우선순위를 가진 항목들을 저장하는 큐
  - FIFO가 아니라 우선순위가 높은 순서로 먼저 나가게 됨



- java.util.PriorityQueue
  - Heap 자료구조
  - 원소들의 natural ordering(오름차순)에 따라 Heap 유지
  - 따라서 모든 원소는 Comparable 인터페이스를 구현해야 함
- java.util.PriorityQueue(Comparator comparator)
  - 명시된 Comparator의 구현에 따라 원소들의 순서를 유지



