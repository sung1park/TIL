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



##### h

- header
- `<h1>`~`<h6>`



##### a

- anchor, hyperlink
- `href` : indicates the link's destination
  - #anchor name 처럼  id를 써서 페이지 내에서 이동 가능
- `target` : 링크를 현재 또는 새 윈도우에서 열지 결정
  - `_blank`, `_self`, `_parent`, `_top`
- `<map>`: 하나의 이미지에 여러 개의 링크를 설정하여, 클릭하는 위치에 따라 서로 다른 링크를 부여
  - `area`: 이미지 영역을 표시
    - `href`, `target`, `shape` 속성
      - `shape`의 값은 `default`, `rect`, `circle`, `poly`



##### li

- 리스트 항목을 명시
- `<ul>`: unordered list 
- `<ol>`: ordered list 
  - `start` :  번호의 시작점을 설정



##### br

- new line



##### form

- 서버에서 처리될 데이터를 제공하는 역할
- `action`, `method`



##### label

- `for` : 라벨을 클릭했을때 목표하는 id에 연결할 수 있음



##### input

- 사용자의 입력을 받는 태그
- `autofocus`: 페이지에 들어왔을때 default로 커서를 띄워놓을 수 있음
- `checked`: 페이지에 들어왔을때 default으로 선택
- `type` 
  - https://www.w3schools.com/tags/tag_input.asp 참고
  - `image`타입은 submit을 기본적으로 수행



##### button

- `input type="button"`과 유사하지만 기본적으로 submit을 수행한다는 점에서 다름



##### select - option

- dropdown 창을 만드는 태그

- `disabled` : 선택할 수 없게 음영처리 할 수 있음



##### table

- 표를 만들때 쓰는 태그
- 태그 내의 데이터들을 모두 로딩해 한번에 보여줘야 할 경우에 사용 (아니면 `div`를 사용)
- `<tr>`, `<td>`, `<th>`
- `<thead>`, `<tbody>`, `<tfoot>`
- 셀 병합 속성 `colspan `, `rowspan`
- `<colgroup>`, `<col>`



##### img

- 이미지를 삽입
- `src` : 이미지 경로를 지정
- `alt` : 이미지를 표시할 수 없을때 대신 보여줄 텍스트
- `height`, `width` 속성
- `figure`: 설명 글을 붙여야 할 대상을 지정
  - `figcaption`: 설명 글

