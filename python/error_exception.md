# Exception

### 에러

##### SyntaxError

- 문법 에러



### 예외

##### ZeroDivisionError

- 0으로 나누고자 할 때 발생

##### NameError

- namespace 상에 이름이 없는 경우

##### TypeError

- 타입 불일치
- argument 누락
- argument 개수 초과
- argument type 불일치

##### ValueError

- 타입은 올바르나 값이 적절하지 않거나 없는 경우

##### IndexError

- 인덱스가 존재하지 않거나 범위를 벗어나는 경우

##### KeyError

- 해당 키가 존재하지 않는 경우

##### ModuleNotFoundError

- 존재하지 않는 모듈을 import 하는 경우

##### ImportError

- Module은 있으나 존재하지 않는 클래스/함수를 가져오는 경우

##### KeyboardInterrupt

- 임의로 프로그램을 종료하였을 때

##### IndentationError

- Indentation이 적절하지 않는 경우

##### Python built-in-exceptions

- https://docs.python.org/ko/3/library/exceptions.html#exception-hierarchy

##### Exception

- 가장 큰 범주의 예외



### 예외 처리 

##### EAFP (Easier to Ask for Forgiveness than Permission)

- 허락보다 용서를 구하는 것이 쉽다.
- 예외 처리를 활용하여 검사를 수행하지 않고, 일단 실행하고 예외 처리를 진행하는 스타일
- 파이썬 코드가 문제 없이 '실행될 것'을 전제로 코드를 실행

```python
my_dict = {
    'key': 'value',
}

# EAFP
try:
    x = my_dict['key']
except KeyError:
    pass

# LBYL
if 'key' in my_dict:
    x = my_dict['key']
else:
    pass
```



- `try ` : 코드를 실행함

- `except` : try문에서 예외가 발생 시 실행함

- `else` : try문에서 예외가 발생하지 않으면 실행함

- `finally` : 예외 발생 여부와 관계없이 항상 실행함

    ```python
    try:
        f = open('nooofile.txt')
    except FileNotFoundError:
        print('해당 파일이 없습니다.')
    else:
        print('파일을 읽기 시작합니다.')
        print(f.read())
        print('파일을 모두 읽었습니다.')
        f.close()
    finally:
        print('파일 읽기를 종료합니다.')
    ```

- 에러 메시지 처리 : `as`를 활용해 원본 에러 메시지를 사용할 수 있음

    ```python
    try:
        empty_list = []
        print(empty_list[-1])
    except IndexError as err:
        print(f'{err}, 오류가 발생했습니다.')
    ```

  

### 예외 발생 시키기

##### raise

- `raise`를 통해 예외를 강제로 발생

  ```
  raise <표현식>(메시지)
  raise ValuError('값 에러 발생')
  ```

##### assert

- `assert`를 통해 예외를 강제로 발생

- `assert`는 상태를 검증하는데 사용되며, 무조건 `AssertionError`가 발생

- 일반적으로 디버깅 용도로 사용

  ```
  assert <표현식>, <메시지>
  # 표현식이 False인 경우 Assertion Error
  ```

- `-O`옵션으로 실행하는 경우, `assert`문과 `__debug__`에 따른 조건부 코드를 제거 후 실행

