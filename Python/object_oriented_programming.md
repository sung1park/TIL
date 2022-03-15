# OOP (Object Oriented Programming)

> 파이썬의 객체 지향 프로그래밍



## 객체 지향 프로그래밍

> Object-Oriented Programming OOP

- 실 세계의 모든 것은 객체간의 상호작용에 의해 이루어진다는 개념 아래 모든 것을 객체로 정의
- 객체들이 서로 관계성을 가지고 시스템을 구성한다
- 개발자로 하여금 쉽게 커스터마이징이 가능하게 하고 유지보수성, 확장성, 재사용성을 증가시켜 생산성을 크게 늘려준 프로그래밍 기법이다.



### 특징

> Abstraction, Encapsulation, Inheritance, Polymorphism

##### Abstraction

- 시스템을 구축하기 위해 필요한 근본적인 요소들을 뽑아내는 과정
- 현실의 다양한 객체들의 공통된 특성을 모아 일반화한다
- 클래스를 정의하는데 중요한 역할을 한다

##### Encapsulation

- 각각 구현한 것들의 내부를 모두 보여주지 않음으로 시스템의 복잡도를 낮춘다(감춘다)
- 메서드를 하나로 묶어 변수와 메서드가 독립적으로 동작하지 않도록 한다
- 정보 은닉

##### Inheritance

- 객체를 정의할 때 기존에 존재하는 객체의 속성과 기능을 상속받아 정의하는 것
- 각 클래스의 공통 부분을 한번에 수정할 수 있게 하여 코드의 재사용성을 높여준다

##### Polymorphism

- 같은 타입 또는 같은 기능의 호출로 다양한 효과를 가져오는 것
- 하나의 인터페이스로 서로 다른 구현을 제공한다
- 메서드 오버로딩 (<u>Overloading</u>)
  - 한 클래스에 같은 이름의 메서드를 여러개 정의, 그 인자의 개수나 유형을 다르게 한다
- 메서드 오버라이딩(<u>Overriding</u>)
  - 상속 관계에 있는 하위 클래스가 상위 클래스의 메서드를 재정의한다



## 객체

> *파이썬은 모두 객체(object)로 이루어져 있다.* *객체(object)는 특정 타입의 인스턴스(instance)이다.*

#### 특징

- 타입(type) : 어떤 연산자(operator)와 조작(method)이 가능한가?
- 속성(attribute) : 객체의 상태/데이터
- 조작법(method) : 특정 객체에 적용될 수 있는 행위. 일반적으로 클래스에 정의된 함수



#### is 연산자

- 객체의 identity 를 검사하는 연산자

```python
type(10) # int
type(10) is int # True
type(0) is bool # False
type(10) is object # False
```



#### isinstance(object, classinfo)

- `classinfo`의 instance이거나 **subclass**인 경우 `True`
- `classinfo`가 tuple인 경우(type으로 구성된) 하나라도 일치하면 `True` 
- `classinfo`가 type이 아니거나 type으로 구성되지 않은 경우 TypeError

```python
isinstance(10, int) # True
isinstance(10, object) # True, 모든 파이썬 클래스는 object 클래스를 상속받음
isinstance(0, (bool, int, complex)) # True
isinstance(0, (bool, 'hi', complex)) # TypeError
```



#### ==, is 의 차이

- `==`
  - 동등한(equal)
  - 변수가 참조하는 객체가 동등한(내용이 같은) 경우 `True`
  - 두 객체가 같아 보이지만 실제로 동일한 대상을 가리키고 있다고 확인해 준 것은 아님
- `is`
  - 동일한(identical)
  - 두 변수가 동일한 객체를 가리키는 경우 `True`



## 클래스

#### 클래스 메서드

```python
class MyClass:
    
    @classmethod
    def class_method(cls, arg1, ...):
```

- 클래스가 사용할 메서드
- `@classmethod` 데코레이터를 사용하여 정의
- 호출 시, 첫번째 인자로 클래스(cls)가 전달됨



#### 스태틱 메서드

```python
class MyClass:
    
    @staticmethod
    def class_method(arg1, ...)
```

- 클래스가 사용할 메서드
- `@staticmethod` 데코레이터를 사용하여 정의
- 호출 시, 어떠한 인자(self, cls)도 전달되지 않음 (클래스 정보에 접근/수정 불가)



✔ 주석과 데코레이터는 완전히 다른 기능입니다. 데코레이터는 실제로 어떤 함수를 감싸는 형태의 또 다른 함수일 뿐입니다. 앞에 at sign(@)을 붙여서 쓰는 건 파이썬 문법으로써 개발자가 데코레이터를 정의하고 사용하기 쉽게끔 제공해주는 문법적 장치(syntatic sugar)라고 생각해주시면 됩니다.



#### 인스턴스 메서드 / 클래스 메서드 / 스태틱 메서드

- 인스턴스 메서드
  - self 매개 변수를 통해 동일한 객체에 정의된 속성 및 다른 메서드에 자유롭게 접근 가능
  - 뿐만 아니라 클래스 자체에 접근할 수 있음
    - 즉, 인스턴스 메서드가 클래스 상태를 수정할 수도 있음
- 클래스 메서드
  - 클래스를 가리키는 cls 매개 변수를 받음
  - cls 인자에만 접근할 수 있기 때문에 객체 인스턴스 상태를 수정할 수는 없음
- 스태틱 메서드
  - 임의 개수의 매개 변수를 받을 수 있지만, self나 친 매개 변수는 사용하지 않음
  - 즉, 객체 상태나 클래스 상태를 수정할 수 없음
  - 일반 함수처럼 동작하지만 클래스의 이름공간에 귀속됨
    - 주로 해당 클래스로 한정하는 용도로 사용



#### 스태틱 메서드는 언제 사용해야 할까?

- 스태틱 메서드는 self, cls 인자를 취하지 않기 때문에 사용에 있어 큰 제약이 있어보임
  - 하지만, 반대로 특정한 메서드가 주변의 다른 것들과 독립적일 수 있음을 뜻하는 것이기도 함
- 스태틱 메서드와 클래스 메서드를 사용하는 것은 개발자의 의도를 전달하는 동시에 개발자가 자신의 의도를 강제해 버그로 인해 설계를 깨뜨리지 않도록 함
- self, cls 인자를 전달하지 않기 때문에 객체 인스턴스, 클래스 상태에 접근할 수 없음을 보장
- 또한 일반 함수를 사용하는 것처럼 실행할 수 있기 때문에 객체 지향 프로그래밍과 절차 지향 프로그래밍 스타일 사이를 연결하는 역할을 하기도 함



## 상속

- 클래스는 상속이 가능하다.
- 모든 파이썬 클래스는 object를 상속 받는다.
- 상속을 통해 객체 간의 관계를 구축한다.
- 부모 클래스의 속성, 메소드가 자식 클래스에 상속되므로 코드 재사용성이 높아진다.

``` python
class ChildClass(ParentClass):
    pass
```



#### isinstance(object, classinfo)

- `classinfo`의 instance이거나 **subclass**인 경우 True



#### issubclass(class, classinfo)

- `class`가 `classinfo`의 subclass면 True
- `classinfo`는 클래스 객체의 튜플일 수 있으며, 그 경우 `classinfo`의 모든 항목을 검사



#### super()

- 자식 클래스에서 부모 클래스를 사용하고 싶은 경우

```python
class Person:
    def __init__(self, name, age, number, email):
        self.name = name
        self.age = age
        self.number = number
        self.email = email
        
class Student(Person):
    def __init__(self, name, age, number, email, student_id):
        # Person 클래스
        super().__init__(name, age, number, email)
        self.student_id = student_id
```



#### 메서드 오버라이딩(method overriding)

- 상속 받은 메서드를 재정의
  - 상속 받은 클래스에서 같은 이름의 메서드로 덮어씀
  - 부모 클래스의 메서드를 실행시키고 싶은 경우 super를 활용



#### 다중 상속



#### 상속 정리

- 파이썬의 모든 클래스는 object로부터 상속됨
- 부모 클래스의 모든 요소(속성, 메서드)가 상속됨
- super()를 통해 부모 클래스의 요소를 호출할 수 있음
- 메서드 오버라이딩을 통해 자식 클래스에서 재정의 가능함
- 상속 관계에서의 이름 공간은 인스턴스, 자식 클래스, 부모 클래스 순으로 탐색
- 파이썬에서는 메서드 오버로딩은 지원하지 않음. 필요가 없을 것으로 생각