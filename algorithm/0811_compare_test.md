# compare test

### Comparable interface

- 원소 스스로가 비교대상이 될 수 있게 기준을 잡아줌

- 기준이 한 가지로 명확할 떄 사용함 (여러 기준을 적용할 수 없음)

- `int compareTo(T other)`를 재정의 해주어야 함

  - 음수 : 타 원소가 크다
  - 0       : 둘이 같다
  - 양수 : 자신이 크다

  ```java
  class Student implements Comparable<Student> {
      int no, score;
      
      public Student(int no, int score) {
          super();
          this.no = no;
          this.score = score;
      }
      
      @Override
      public int compareTo(Student o) {
          return this.no - o.no;
      }
  }
  ```

  

### Comparator interface

- 직접 두 개를 비교할 수 있음

- 기준이 두 가지 이상일 때 사용함

- `int compare(T o1, T o2)`를 재정의 해주어야 함

  - 음수 : o2 원소가 크다
  - 0      : 둘이 같다
  - 양수 : o1 원소가 크다

  ```java
  class StudentComparator implements Comparator<Student> {
      @Override
      public int compare(Student o1, Student o2) {
          return o1.no - o2.no;
      }
  }
  ```

  

