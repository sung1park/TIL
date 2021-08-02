# selector / combinator

> html 문서에서 특정한 요소를 선택하여 스타일링 하기 위해 사용되는 선택자와 결합자



### 선택자 (selector)

```html
<style>
  /* 전체 선택자 */
  * {
    color: red;
  }

  /* 요소 선택자 */
  h2,
  h3 {
    color: orange;
  }
</style>
```

```html
<style>
  /* 클래스 선택자 */
  .green {
    color: green;
  }

  /* id 선택자 */
  #purple {
    color: purple;
  }

  /* 자식 결합자 */
  .box > p {
    font-size: 30px;
  }

  /* 자손 결합자 */
  .box p {
    color: blue;
  }
</style>
```



### 결합자 (combinators)

##### 자손 결합자

- selectorA 하위 모든 selectorB 요소

##### 자식 결합자

- selectorA 바로 아래의 selectorB 요소

##### 일반 형제 결합자

- selectorA의 형제 요소 중 뒤에 위치하는 selectorB 요소를 모두 선택

##### 인접 형제 결합자

- selectorA의 형제 요소 중 바로 뒤에 위치하는 selectorB 요소를 선택



```html
<!--자손 결합자--> A B { }
<!--자식 결합자--> A > B { }
<!--일반 형제 결합자--> A ~ B { }
<!--인접 형제 결합자--> A + B { }
```



### CSS 적용 우선순위 (cascading order)

1. 중요도 (Importance)
   - !important
2. 우선 순위 (Specificity)
   - 인라인 > id 선택자 > **class 선택자**, 속성 선택자, pseudo-class > 요소 선택자 pseudo-element
3. 소스 순서
   - 나중에 선언된 것을 우선으로 



### CSS 상속

- 속성 중에는 상속이 되는 것과 되지 않는 것들이 있다.
- 상속 되는 것 예시
  - Text 관련 요소(font, color, text-align), opacity, visibility 등
- 상속 되지 않는 것 예시
  - Box model 관련 요소(width, height, margin, padding, border, box-sizing, display)
  - position 관련 요소(position top/right/bottom/left, z-index) 등



