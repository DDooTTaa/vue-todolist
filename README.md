# vue-todolist

> A Vue.js project

## Build Setup

```bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build
```

For detailed explanation on how things work, consult the [docs for vue-loader](http://vuejs.github.io/vue-loader).

---

vue3 에서 vue2 로 바꾸는 방법

vue --version
npm r -g @vue/cli
npm i -g vue-cli

vue2 는 프로젝트명 지을 때
vue init (template) (project name)

[template 종류]

webpack : 모듈번들러를 hot-reload, linting, test, CSS추출기능 등 대부분의 기능을 갖추고 있는 webpack으로 사용하고, vue-loader를 포함하는 template
webpack-simple : 단순히 webpack과 vue-loader를 포함하는 template. 간단히 프로토 타입을 만들때 사용
browserify : 모듈번들러를 hot-reload, linting, test,CSS추출기능 등 대부분의 기능을 갖추고 있는 browserify로 사용하고 vuetify를 포함하는 template
browserify-simple : 단순히 browserify와 vuetify를 포함하는 template. 간단히 프로토 타입을 만들때 사용
simple : 가장단순하게 html파일에 vue 설정만 가짐

project name -> 소문자


알게 된 것

1. Localstorage 를 이용한 방법 - 전역 state를 사용하는 것처럼, Localstorage에 키 벨류 값을 뿌린 후 다른 컴포넌트에서 get으로 가져오는 방법
  *장점: 저장이 가능하다
  *단점: 리소스 낭비가 심하다.

##설계대로 작업했을 경우 문제점

---

##설계와 달라진 것들

-- setTodo 에 버튼보다 Keypress 를 이용해 엔터를 누를 경우 todo 를 추가하는 게 더 직관적이라는 생각이 들어 버튼 삭제

-- destroyAll() 메소드와 insertTodo() 메소드를 Header 에서 정의하는 것보다 App 에서 정의하는 게 괜찮다 판단
 ※ todos 변수를 Bodylist 변수에 전달해야 하기 때문

--Delete 컴포넌트는 변수를 통해 지우지 않고 event.target.parentElement.remove() 를 통해 HTML 상위 태그를 이용해서 지움


##Vue 정리

-- vue

v-bind 속성은 뷰 인스턴스의 데이터 속성을 해당 HTML 요소에 연결할 때 사용한다.
v-on 속성은 해당 HTML 요소의 이벤트를 뷰 인스턴스의 로직과 연결할 때 사용한다.
'v-model' 을 쓰면 양방향 바인딩이 된다.

-- 공식 문서에서는 한국어 입력을 다룰 때 v-bind 와 v-on 을 직접 연결해서 사용하는 것을 권고
https://joshua1988.github.io/web-development/vuejs/v-model-usage/


Computed 와 Watch

Watch -> 명령형 프로그램
Computed -> 선언형 프로그램
https://v3.ko.vuejs.org/guide/computed.html#computed-%E1%84%89%E1%85%A9%E1%86%A8%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%B4-setter


상위 컴포넌트와 하위 컴포넌트의 데이터 전달 방법 props 와 $emit,
$emit 은 하위 컴포넌트에서 상위 컴포넌트로 데이터를 전달,
vue의 단방향 데이터 흐름에 어긋나 사용을 지양. -> vuex 를 통한 State Manage 필요

##코드 출처

https://simplevue.gitbook.io


##온라인 강좌

https://www.inflearn.com/course/Age-of-Vuejs?inst=72986832&utm_source=blog&utm_medium=githubio&utm_campaign=captianpangyo&utm_term=banner
