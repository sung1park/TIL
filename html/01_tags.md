# HTML tags

### 시맨틱 태그

- HTML5에서 의미론적 요소를 담은 태그가 등장함 (`<div>`를 대체)
- 개발자나 사용자 뿐만 아니라 브라우저에게도 해석하기 좋은 의미있는 코드를 작성할 수 있음
- 웹 접근성 측면에서도 고려해야 할 사항
- 대표적인 태그들
  - header : 문서 전체나 섹션의 헤더
  - nav : 내비게이션
  - aside : 사이드에 위치한 공간, 메인 콘텐츠와 관련성이 적은 콘텐츠
  - section : 문서의 일반적인 구분, 컨텐츠의 그룹을 표현
  - article : 문서, 페이지, 사이트 안에서 독립적으로 구분되는 영역
  - footer : 문서 전체나 섹션의 푸터 (마지막 부분)



-----

##### !DOCTYPE  html

- html5 문서임을 명시



##### a

- hyperlink

- `href`: indicates the link's destination



##### li

- 리스트 항목을 명시
- `ul`: unordered list 
- `ol`: ordered list 



##### br

- new line



##### form

- 서버에서 처리될 데이터를 제공하는 역할
- `action`, `method` 속성을 가짐



##### label

- `for` : 라벨을 클릭했을때 목표하는 id에 연결할 수 있음



##### input

- 사용자의 입력을 받는 태그
- `autofocus` : 페이지에 들어왔을때 default로 커서를 띄워놓을 수 있음
- `checked` : 페이지에 들어왔을때 default으로 선택
- `type` 
  - https://www.w3schools.com/tags/tag_input.asp 참고



##### select - option

- dropdown 창을 만드는 태그

- `disabled` 속성 : 선택할 수 없게 음영처리 할 수 있음



##### table

- 표를 만들때 쓰는 태그
- `tr`: defines a table row
- `th`: defines a table header
- `td`: defines a table cell