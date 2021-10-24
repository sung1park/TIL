# Cookie & HttpSession



## Cookie

#### 구성 요소

- 이름
- 값
- 유효기간 : 초, 시간이 만료되면 파일이 지워지는게 아니라 유효하지 않게됨
- 도메인
- 경로



#### 동작 순서

- Client가 페이지 요청
- WAS는 Cookie 생성
- Http Header에 Cookie를 넣어 응답
- Browser는 넘겨받은 Cookie를 PC에 저장하고, 다시 WAS가 요청할 때 요청과 함께 Cookie 전송 (Request Header)
- Browser가 종료되어도 Cookie의 만료 기간이 남아 있다면 Client는 계속 보관
- 동일 사이트 재방문시 Client의 PC에 해당 Cookie가 있는 경우, 요청 페이지와 함께 Cookie를 전송



#### 주요 기능 (javax.servlet.http.Cookie)

생성 : Cookie cookie = new Cookie(String name, String value)

값 변경/ 얻기 : cookie.setValue(String value); / String value = cookie.getValue();



