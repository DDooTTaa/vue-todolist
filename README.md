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
 상위 컴포넌트와 하위 컴포넌트의 데이터 전달 방법은 props 와 $emit 이다. 여기서 $emit 은 하위 컴포넌트에서 상위 컴포넌트로 데이터를
 전달하는데 vue의 단방향 데이터 흐름에 어긋나니 사용을 지양해야 한다고 한다. -> vuex 를 통한 State Manage 필요

---

##설계와 달라진 것들

-- setTodo 에 버튼보다 Keypress 를 이용해 엔터를 누를 경우 todo 를 추가하는 게 더 직관적이라는 생각이 들어 버튼 삭제

-- destroyAll() 메소드와 insertTodo() 메소드를 Header 에서 정의하는 것보다 App 에서 정의하는 게 괜찮다 판단
 ※ todos 변수를 Bodylist 변수에 전달해야 하기 때문

--Delete 컴포넌트는 변수를 선언하지 않고 event.target.parentElement.remove() 를 통해 html 요소로 접근해서 지움
