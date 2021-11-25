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
