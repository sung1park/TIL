# crawling

> 파이썬을 이용한 웹 페이지 크롤링



### requests 라이브러리

1. bash에서 pip install 명령어를 통해 requests 라이브러리를 설치한다.

```bash
$ pip install requests
```

2. 라이브러리를 import 하여 사용한다.

```python 
import requests
requests.get(주소)
requests.get(주소).text
requests.get(주소).content
requests.get(주소).status_code
```

- get을 했을때 돌아오는 숫자에 따라 의미가 다르다. 200번대의 경우 원활하게 요청과 응답이 되었다는 뜻이고, 400번대의 경우 클라이언트의 요청에 문제가 있다는 뜻, 500번대의 경우 서버에 문제가 있다는 의미이다.

##### params 이용하기

```python
url = 'https://search.naver.com/search.naver'
params = {
    'where': 'news',
    'query': '코로나',
    'start': 2
}
requests.get(url=url, params=params)
```

- query문을 포함한 긴 url 대신 dictionary 형태의 params를 전달해 줄 수 있다.



### BeautifulSoup

- 문서를 python이 읽기 좋게 바꿔주는 기능을 담은 라이브러리

1. bash에서 pip install 명령어를 통해  라이브러리를 설치한다.

```bash
$ pip install beautifulsoup4
```

2. 라이브러리를 import 하여 사용한다.

```python
from bs4 import BeautifulSoup
BeautifulSoup(문서)
BeautifulSoup.select(selector 경로)
BeautifulSoup.select_one(selector 경로)
```

- 웹 페이지에서 경로를 가져올때는 'copy selector'를 이용해 필요한 요소의 ID를 가져온다.
- 문서를 가져올 때는 문서의 형식에 맞춰서 아래와 같이 파싱을 해주어야 한다.

```python
data = BeautifulSoup(response.text, 'html.parser')
```



### crawling의 단점

1. 브라우저가 아닌 상황에서 필요 없는 데이터가 너무 많음
2. 데이터를 얻기 위한 추후 작업이 필요함

