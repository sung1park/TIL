# box model

>모든 html 요소는 box 형태로 되어있음
>
>하나의 박스는 네 부분(영역)으로 이루어짐



### box model 구성

- margin : 테두리 바깥의 외부 여백. 배경색을 지정할 수 없다.
- border : 테두리 영역
- padding : 테두리 안쪽의 내부 여백. 요소에 적용된 배경색, 이미지는 padding까지 적용
- content : 글이나 이미지 등 요소의 실제 내용



##### margin

```css
.margin {
  margin-top: 10px;
  margin-right: 20px;
  margin-bottom: 30px;
  margin-left: 40px;
}

<!--shorthand로 표현 가능-->
<!--상하좌우-->
.margin-1 {
    margin: 10px;
}
<!--상하,좌우-->
.margin-2 {
    margin: 10px 20px;
}
<!--상,하,좌우-->
.margin-3 {
    margin: 10px 20px 30px;
}
<!--상,하,좌,우-->
.margin-4 {
    margin: 10px 20px 30px 40px;
}
```

##### padding

```css
.margin-padding {
  margin: 10px;
  padding: 30px; 
}
```

##### border

```css
.border {
  border-width: 2px;
  border-style: dashed;
  border-color: black;
}

<!--shorhand로 표현 가능-->
.border {
    border: 2px dashed black;
}
```





### box-sizing

- 기본적으로 모든 요소의 box-sizing은 content-box
  - Padding을 제외한 순수 contents 영역만을  box로 지정
- 다만, 우리가 일반적으로 영역을 볼 때는 border 까지의 너비를 100px 보는 것을 원함
  - box-sizing을 border-box로 지정

```css
.box-sizing {
    box-sizing: border-box;
}
```



### 마진 상쇄

- 두 개의 블럭이 상하로 위치했을때, 각각의 margin 값 중 큰 마진값으로 결합되는 현상
- 좌우로는 마진상쇄가 이뤄지지 않음