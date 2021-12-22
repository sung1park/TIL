# Compare Test

> java.lang.Comparable, java.util.Comparator
>
> 두 원소를 비교하거나 iterable 객체를 정렬할 때 기준을 세우기 위해 사용되는 인터페이스



### Comparable interface

- 자기 자신과 다른 매개변수 객체를 비교

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

- 두 매개변수 객체를 비교

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

  

