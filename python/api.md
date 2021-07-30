# API 

> API를 활용하여 정보 가져오기



### JSON (Javascript Object Notation)

- JSON은 클라이언트와 서버가 정보를 주고 받을때 약속한 형식, 프로토콜이다.
- JSON 파일의 내용은 `str` 타입이다. 
- 다음과 같이 *dictionary*와 비슷한 형태를 가진다. 하지만 JSON에서는 `'`를 사용한다.

```json
{
  "name": "michael",
  "age": 69,
  "count": 233482
}
```

- 아래와 같은 구문을 통해 dictionary로 바꿀 수 있다.

```python
response = request.get(url).json()
```



### requests 모듈

- `params=`, `headers=` 에 `dict`형태로 패러미터와 헤더를 입력하여 요청할 수 있다.

```python
requests.get(url, params=payload, headers=headers)
```

