# Vue.js

> Javascript Framework



### MVVM 패턴

![MVVM](img/mvvm.png)

- Model + View + ViewModel
- Model : 순수 자바스크립트 객체
- View : 웹페이지의 DOM
- ViewModel : Vue의 역할



![mvcmvvm](img/mvcmvvm.png)

- 기존에는 자바스크립트로 view에 해당하는 DOM에 접근함거나 수정하기 위해 jQuery와 같은 라이브러리를 이용
- Vue는 view와 Model을 연결하고 자동으로 바인딩 하므로 양방향 통신을 가능하게 함



### Vue.js 설치

- `<script>` include (Download, CDN)
- NPM
- CLI



### Chrome Extension

- Vue.js devtools
  - 크롬에서 디버깅 할 수 있음



### Vue Instance 생성

```vue
<script>
	new Vue({
        el: '#app',
        data() {
            return {
                message: 'Hello Vue!',
            }
        }
    })
</script>
```

##### 속성

- `el`: Vue가 적용될 요소 지정
- `data`: Vue에서 사용되는 정보 저장. 객체 또는 함수 형태
- `template`: 화면에 표시할 html, css 등의 마크업 요소를 정의하는 속성
- `methods`: 화면 로직 제어와 관계된 method를 정의하는 속성. 이벤트 처리나 화면 동작과 관련된 로직을 추가
- Life cycle에 맞춰 실행되는 함수들



### Vue Instance의 유효 범위

- el 속성에 



### Life Cycle

![image-20211104171659932](img/image-20211104171659932.png)

- beforeCreate : Vue Instance가 생성되고 각 정보의 설정 전에 호출
- created : Vue Instance가 생성된 후 데이터들의 설정이 완료된 후 호출
- beforeMount : 마운트가 시작되기 전에 호출
- mounted : 지정된 element에 Vue Instance 데이터가 마운트 된 후에 호출
- beforeUpdate : 데이터가 변경될 때 virtual DOM이 랜더링
- updated : Vue에서 관리되는 데이터가 변경되어 DOM이 업데이트 된 상태
- beforeDestroy : Vue Instance가 제거되기 전에 호출
- destroyed : Vue Instance가 제거된 후 호출





### Directives

- 데이터 바인딩의 기본 형태는 'Mustache' 구문 `{{ <내용> }}`



##### v-once

```vue
<span v-once>다시는 변경하지 않겠습니다. : {{ msg }}</span>
```

- 데이터 변경 시 업데이트 되지 않는 DOM을 지정



##### v-text, v-html

```vue
<div id="app">
    <!-- msg: <h2>Hello Vue!</h2> -->
    <div v-text="'msg: ' + msg"></div>
    <!-- Hello Vue! -->
    <div v-html="msg"></div>
</div>
<script>
	...
    msg: '<h2>Hello Vue!</h2>'
    ...
</script>
```

- `v-text`는 data의 변수를 불러오지만 텍스트 그 자체로 가져옴
- `v-html`은 data의 변수를 html로 가져옴



##### v-model

```vue
<input type='text' v-model='message'>
입력 메세지 : {{ message }}
```

- form의 input, textarea 같은 곳에 양방향 바인딩 처리를 위해 사용



##### v-bind

```vue
<div id="app">
    <a v-bind:href="link1">네이버로 가기</a>
    <a :href="link1">네이버로 가기</a>
    <div v-bind:[key]="value"></div>
</div>
<script>
	...
    key: 'id',
    value: 'linkToNaver',
    link1: 'https://www.naver.com',
	...
</script>
```

- data의 변수와 바인딩 처리를 위해 사용
- 약어로 `:` 사용 가능
- `[<attrname>]`을 통해 속성 명을 변수에서 가져올 수 있음. 이 때 속성 값도 변수에 있어야 함



##### v-show

```vue
<div id="app">
    <div v-show="isShow">{{ msg }}</div>
</div>
<script>
	...
    isShow: true,
    msg: 'Hello!'
    ...
</script>
```

- `v-show="condition"`에서 조건이 true면 화면에 보이고, false면 화면에서 숨김
- css의 `display: none`과 같이 작용



##### v-if, v-else-if, v-else

```vue
<div id="app">
    <div>
        <span>나이: </span>
        <input type="number" v-model="age">
    </div>
    <div>
        <span>요금: </span>
        <span v-if="age < 10">3000원</span>
        <span v-else-if="age < 20">7000원</span>
        <span v-else-if="age < 65">10000원</span>
        <span v-else>무료</span>
    </div>
</div>
<script>
	...
    	age: 0,
    ...
</script>
```

- `if` ~ `else if` ~ `else` 구문
- 조건에 맞는 요소들만 보여준다는 점에서 v-show와 비슷하지만, v-show와는 다르게 조건이 false일 경우 엘리먼트를 렌더링하지 않고 조건 변경 시 삭제한다
- template를 지원한다



##### v-for

```vue
<div id="app">
    <ul>
        <li v-for="(item, index) in items" :key="index">
        	{{ index }} : {{ item.key }}
        </li>
    </ul>
</div>
<script>
	...
    items = [
    	item1: { key1: value1, key2, value2, ... }
        ...
    ]
    ...
</script>
```

- key를 왜 써야 하는가?

  - Vue가 예측 가능하게 작동하도록 하기 위해 (Edge case에서)
  - https://kr.vuejs.org/v2/style-guide/#v-for-%EC%97%90-key-%EC%A7%80%EC%A0%95-%ED%95%84%EC%88%98

- v-if와 v-for를 같이 쓰지 말것

  - https://kr.vuejs.org/v2/style-guide/#v-if%EC%99%80-v-for%EB%A5%BC-%EB%8F%99%EC%8B%9C%EC%97%90-%EC%82%AC%EC%9A%A9%ED%95%98%EC%A7%80-%EB%A7%88%EC%84%B8%EC%9A%94-%ED%95%84%EC%88%98

  - Vue가 directive를 처리할 때 v-for가 v-if보다 우선순위가 높음

  - 쓸데 없는 for문을 만들어 조건에 맞지 않는 항목을 삭제하다 보니 성능이 떨어짐

  - 'computed' 속성을 이용하기

    ```vue
    <!-- items의 객체들 중 data의 key의 value값과 같은 객체들을 찾아냄 -->
    computed: {
    	matchItems: function() {
    		return this.items.filter(item => item.key === this.key)
    	}
    }
    ```

    

##### template

```vue
<template v-if="count % 2 == 0">
	<span>여러개의 태그를 묶어서 처리해야 할 경우</span>
	<span>각각의 태그에 v-if를 달 필요가 없다</span>
</template>
```

- 여러개의 태그를 묶어서 처리해야 할 경우 사용한다



##### v-cloak

```vue
<style>
    [v-cloak]::before {
        content: '로딩중,,,',
    }
</style>
<div id="app">
    <div v-cloak>
        <h1> {{ msg }} </h1>
    </div>
</div>
```

- Vue instance가 준비될 때 까지 mustache 바인딩을 숨기는데 사용한다