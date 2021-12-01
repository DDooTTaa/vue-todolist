
```bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build
```

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


##설계와 달라진 것들 (추가 사항)

-- setTodo 에 버튼보다 Keypress 를 이용해 엔터를 누를 경우 todo 를 추가하는 게 더 직관적이라는 생각이 들어 버튼 삭제
    -> Keypress.enter 사용

-- destroyAll() 메소드와 insertTodo() 메소드를 Header 에서 정의하는 것보다 App 에서 정의하는 게 괜찮다 판단
 ※ todos 배열을 Bodylist 변수에 전달해야 하기 때문

--Delete 컴포넌트는 변수를 통해 지우지 않고 event.target.parentElement.remove() 를 통해 HTML 상위 태그를 이용해서 지움
    -> event target 안 쓰고 this.arr.splice(index, 1) 로 바꿈. BodyList에 저장
    -> Delete는 컴포넌트가 아닌 메소드이기에 BodyList 에 추가

--객체로 선언된 todos를 배열로 다시 바꿈

-- props를 바꾸지 않고 watch로 데이터 관리 watch 는 후술

--업데이트 인풋 박스가 바뀔 때마다 라벨도 따라 바뀌는 문제 해결 (Ref.현석)
  -> v-model 에 양방향 바인딩으로 모델까지 끌고 가지 않고 엔터키가 눌릴 경우에 데이터 전달

-- 업데이트 인풋 박스에서 ESC 를 누르면 input 데이터가 이전으로 돌아가도록 함 (구현 완료)

##Vue 정리

-- vue

v-bind 속성은 뷰 인스턴스의 데이터 속성을 해당 HTML 요소에 연결할 때 사용한다.
v-on 속성은 해당 HTML 요소의 이벤트를 뷰 인스턴스의 로직과 연결할 때 사용한다.
'v-model' 을 쓰면 양방향 바인딩이 된다.

-- 공식 문서에서는 한국어 입력을 다룰 때 v-bind 와 v-on 을 연결해서 사용하는 것을 권고
https://joshua1988.github.io/web-development/vuejs/v-model-usage/

Object로 받았을 때 todos 바꾸기

-> Object 의 요소로 접근해 바꾸면 양방향 바인딩이 됨

Array로 받았을 때 todos 바꾸기

-> Array의 요소로 접근 시 todos 의 값은 바뀌지 않고 Update 의 Input 값만 바뀐 상태로 저장됨
-> emit 으로 부모 컴포넌트의 전달, v-model를 v-bind와 v-on으로 수정 후 작업 event.target 으로 시도해봄


Computed 와 Watch

Watch -> 명령형 프로그램
Computed -> 선언형 프로그램

https://v3.ko.vuejs.org/guide/computed.html#computed-%E1%84%89%E1%85%A9%E1%86%A8%E1%84%89%E1%85%A5%E1%86%BC%E1%84%8B%E1%85%B4-setter


상위 컴포넌트와 하위 컴포넌트의 데이터 전달 방법 props 와 $emit,
$emit 은 하위 컴포넌트에서 상위 컴포넌트로 데이터를 전달,
vue의 단방향 데이터 흐름에 어긋나 사용을 지양. -> vuex 를 통한 State Manage 필요

##코드 출처

https://simplevue.gitbook.io(참고만 함)


##온라인 강좌

https://www.inflearn.com/course/Age-of-Vuejs?inst=72986832&utm_source=blog&utm_medium=githubio&utm_campaign=captianpangyo&utm_term=banner
