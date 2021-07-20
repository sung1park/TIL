# to find methods for an object

> 객체의 클래스가 가지는 메서드와 속성을 찾는 방법

```python
import requests
res = requests.get('https://www.google.com')
```

위의 코드에서 `res`가 갖고 있는 메서드를 찾아보기 위해 다음과 같은 방법이 있다.

- `dir()`함수를 사용하기
  - `dir(res)`를 작성해 `res`가 가지고 있는 속성과 메서드를 모두 알 수 있다. 하지만 이는 그 속성과 메서드가 무슨 역할을 하는지 추측으로 알아야 하기 때문에 실제로 사용하기는 어렵다.

- 공식 문서를 이용하기

  - 가장 좋은 방법은 공식 문서를 참고해서 사용가능한 메서드를 확인하는 것이다.

  - `requests`의 공식 문서

    https://docs.python-requests.org/en/latest/api/

