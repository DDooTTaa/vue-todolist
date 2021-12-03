

## Vue 정리

https://kr.vuejs.org/v2/guide/components.html

https://v3.ko.vuejs.org/guide/introduction.html

+ vue 인스턴스의 라이프사이클

https://v3.ko.vuejs.org/api/options-lifecycle-hooks.html#beforecreate

beforecreate() = 인스턴스가 생성되기 전

created() = 인스턴스 생성, 데이터 사용 가능

beforeMount() = div태그 #app의 html 코드가 생성되기 전

mount() = html코드가 div태그 #app에 html 코드가 찍혀있는 상태

beforeupdate() = 데이터가 업데이트 되기 전

updated() = 되고난후

beforedestroy() = 해당 페이지를 종료하기 전

destroy() = 해당 페이지가 종료된 상태


### Directives

v- 접두사가 있는 특수 속성

v-bind = 뷰 인스턴스의 데이터 속성을 해당 HTML 요소에 연결할 때 사용.

````
ex) <update-todos v-bind:text="text" v-bind:index="index" />
````

v-on = 해당 HTML 요소의 이벤트를 뷰 인스턴스의 로직과 연결할 때 사용.
````
ex) <a v-on:click="doSomething"> ... </a>
    <input @keypress.enter="updateList" />
````

'v-model' 을 쓰면 양방향 바인딩.
````
ex) <input type="text" placeholder="Your Todo" v-model="todo" @keypress.enter="setTodo"

````

- 공식 문서에서는 한국어 입력을 다룰 때 v-bind 와 v-on 을 연결해서 사용하는 것을 권고
https://vuejs.org/v2/guide/syntax.html#v-bind-Shorthand

## 컴포넌트 작성


상위 컴포넌트와 하위 컴포넌트의 데이터 전달 방법 props 와 $emit,
$emit 은 하위 컴포넌트에서 상위 컴포넌트로 데이터를 전달,
vue의 단방향 데이터 흐름에 어긋나 사용을 지양.

---
***모든 props는 하위 속성과 상위 속성 사이의 단방향 바인딩이어야 함.***

---
 상위 속성이 업데이트되면 하위로 흐르게 만들어 하위 컴포넌트가 실수로 부모의 상태를 변경하여 앱의 데이터 흐름을 추론하기 어렵게 만드는 것을 방지

* 방지 방법

하위 컴포넌트에서 props를 로컬 데이터 속성으로 사용

```
props: ['initialCounter'],
data: function () {
return { counter: this.initialCounter }
}
```
```
props: ['size'],
computed: {
  normalizedSize: function () {
    return this.size.trim().toLowerCase()
  }
}
```

---

자바 스크립트의 객체와 배열은 참조로 전달되므로 prop가 배열이나 객체인 경우 하위 객체 또는 배열 자체를 부모 상태로 변경하면 부모 상태에 **영향을 준다**.

---

### data 는 반드시 함수여야 한다

-> 재사용 되었을 때 각각의 인스턴스를 따로 만들기 위해. 값이면 실행이 되지 않는다.

### Computed, Watch

https://v3.ko.vuejs.org/guide/computed.html#computed-%E1%84%89%E1%85%A9%E1%86%A8%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%B4-setter


## 그 외 알게 된 것

Localstorage 를 이용한 방법 - 전역 state를 사용하는 것처럼, Localstorage에 키 벨류 값을 뿌린 후 다른 컴포넌트에서 get으로 가져오는 방법
* -장점: 저장이 가능하다

* -단점: 리소스 낭비가 심하다.

### vue 3 -> vue 2

vue --version
npm r -g @vue/cli
npm i -g vue-cli

vue2 는 프로젝트명 지을 때
vue init (template) (project name)

+ template 종류

webpack : 모듈번들러를 hot-reload, linting, test, CSS추출기능 등 대부분의 기능을 갖추고 있는 webpack으로 사용하고, vue-loader를 포함하는 template
webpack-simple : 단순히 webpack과 vue-loader를 포함하는 template. 간단히 프로토 타입을 만들때 사용
browserify : 모듈번들러를 hot-reload, linting, test,CSS추출기능 등 대부분의 기능을 갖추고 있는 browserify로 사용하고 vuetify를 포함하는 template
browserify-simple : 단순히 browserify와 vuetify를 포함하는 template. 간단히 프로토 타입을 만들때 사용
simple : 가장단순하게 html파일에 vue 설정만 가짐

project name -> 소문자

##  설계와 달라진 것들 (추가 사항)

-- setTodo 에 버튼보다 Keypress 를 이용해 엔터를 누를 경우 todo 를 추가하는 게 더 직관적이라는 생각이 들어 버튼 삭제
    -> Keypress.enter 사용

-- destroyAll() 메소드와 insertTodo() 메소드는 App 에서 정의해야 함
 ※ Model 인 App 에서 데이터가 변경되는 부분을 전부 처리해야 한다.

--Delete 컴포넌트는 변수를 통해 지우지 않고 event.target.parentElement.remove() 를 통해 HTML 상위 태그를 이용해서 지움
    -> event target 안 쓰고 this.arr.splice(index, 1) 로 바꿈. App에서 실행
    -> Delete는 컴포넌트가 아닌 메소드이기에 BodyList 에 추가

--todos는 객체가 아닌 배열이 맞다.

-- props를 바꾸지 않고 watch로 데이터 관리
   -> watch 를 사용할 필요가 없었기 때문에 watch 를 제거함. watch -> 데이터가 변경될 경우에 메소드를 실행하기 위해 사용해야 함

--업데이트 인풋 박스에 value가 바뀔 때마다 라벨도 따라 바뀌는 문제 해결
  -> v-model 에 양방향 바인딩으로 모델까지 끌고 가지 않고, 엔터가 눌릴 때 데이터 전달

-- 업데이트 인풋 박스에서 ESC 를 누르면 input 데이터가 이전으로 돌아가도록 함

--

## Code Convention

style Checklist

- [x]  CamelCase 를 사용한다.
- [x]  Function 선언은 다음과 같이 한다.중괄호 뒤에 띄어쓰기 testFunction() {}
- [x]  조건문 선언은 다음과 같이 한다. 대괄호 시작과 끝에 띄어쓰기 if(true) {} else if() {} else {}
- [x]  문자열은 작은 따옴표를 쓴다. const test = ‘test String’;
- [x]  코드의 끝은 항상 세미콜론을 입력한다.
- [x]  변수를 재 할당 하는경우 let 을 사용하고 그 외에는 const를 사용한다.(var 사용금지)
- [x]  상수의 변수명은 대문자를 사용한다.
- [x]  변수 선언은 한줄에 하나씩만 한다.( let test1=a, test2=b 이렇게 쓰면 안됨)
- [x]  변수 대입문은 띄어쓰기를 사용한다.( let test = 100;)
- [x]  엔터키를 사용한 공백은 한줄 이상 쓰지 않는다.
- [x]  주석을 생활화 한다.

## 구현 못 한 부분

-- 수정 도중 삭제 누를 경우 다음 인덱스에 인풋창이 열림
 -> 수정 도중 update 에 index 받아와 Delete 버튼을 없애면 막을 수 있을 것 같음

-- 수정 누를 경우 인풋창으로 포커스
 -> ref 를 사용하면 가능할 것 같음

## 온라인 강좌

https://www.inflearn.com/course/Age-of-Vuejs?inst=72986832&utm_source=blog&utm_medium=githubio&utm_campaign=captianpangyo&utm_term=banner


