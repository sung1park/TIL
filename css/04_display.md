# CSS display

> html 요소들을 시각적으로 어떻게 보여줄지 결정하는 속성
>
> 모든 요소는 네모이고, 어떻게 보여지는지(display)에 따라 문서에서의 배치가 달라질 수 있다.



### display: block

- 줄바꿈이 일어나는 요소
- 화면 크기 전체의 가로 폭(100%)을 차지한다.
- 블록 레벨 요소 안에 인라인 레벨 요소가 들어갈 수 있음
- 블록 레벨 요소 :  div / ul, ol, li / p / hr / form 등



### display: inline

- 줄 바꿈이 일어나지 않는 행의 일부 요소
- content 너비만큼 가로 폭을 차지한다.
- width, height, margin-top, margin-botton을 지정할 수 없다.
- 상하 여백은 line-height로 지정한다.
- 인라인 레벨 요소 : span / a / img / input, label / b, em, i , strong 등



### display: inline-block

- block과 inline 레벨 요소의 특징을 모두 갖는다.
- inline 처럼 한 줄에 표시 가능하며,
- block처럼 width, height, margin 속성을 모두 지정할 수 있다.



### display: none

- 해당 요소를 화면에 표시하지 않는다. (공간조차 사라진다.)
- 이와 비슷한 `visibility: hidden`은 해당 요소가 공간은 차지하나 화면에 표시만 하지 않는다.



