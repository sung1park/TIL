# module

### 모듈

- 특정 기능을 파이썬 파일(.py) 단위로 작성한 것

### 패키지

- 특정 기능과 관련된 여러 모듈의 집합
- 패키지 안에는 또 다른 서브 패키지를 포함



### 파이썬 표준 라이브러리(Python Standard Library, PSL)

- 파이썬에 기본적으로 설치된 모듈과 내장 함수



### 파이썬 패키지 관리자(pip)

- PyPI(Python Package Index)에 저장된 외부 패키지들을 설치하도록 도와주는 패키지 관리 시스템

- 패키지 설치

  ```bash
  $ pip install SomePackage
  $ pip install SomePackage==1.0.5
  $ pip install 'SomePackage>=1.0.4'
  # 버전을 명시해서 설치할 수 있음
  ```

- 패키지 삭제

  ```bash
  $ pip uninstall SomePackage
  ```

  - 패키지를 업그레이트 하는 경우 과거 버전은 자동으로 삭제

- 패키지 목록 및 특정 패키지 정보

  ```bash
  $ pip list
  $ pip show SomePackage
  ```

- 패키지 freeze

  ```bash
  $ pip freeze
  $ pip freeze > requirements.txt
  $ pip install -r requirements.txt
  ```

  - 설치된 패키지의 비슷한 목록을 만들지만, pip install에서 활용되는 형식으로 출력
  - 해당하는 목록을 requirements.txt(관습적으로)으로 만들어 관리함
  - 두 대 이상의 컴퓨터에서 같은 환경을 만들때 사용

