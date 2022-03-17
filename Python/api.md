# API 

> API를 활용하여 정보 가져오기



## requests 모듈

- `params=`, `headers=` 에 `dict`형태로 패러미터와 헤더를 입력하여 요청할 수 있다.

```python
requests.get(url, params=payload, headers=headers)
```



## JSON (Javascript Object Notation)

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



#### JSON과 딕셔너리 변환

```python
import json
```

`json.loads()`: JSON에서 딕셔너리로 (load string)

`json.dumps()`: 딕셔너리를 JSON으로 (dump string)



## CSV (Comma Separated Value)

- 각 열이 특정한 의미를 가지는 형식

- `,`로 열을 구분하며, `|`와 같은 다른 구분 문자(delimiter)를 사용할 수도 있다
- 데이터에 `,`가 포함된 경우 `""`를 이용해 데이터를 감싼다
- `JSON`과 비교하면 같은 데이터를 저장해도 용량이 작음



#### 읽기

```python
import csv

with open('movies.csv') as file:
    	reader = csv.reader(file, delimiter=',')
```

