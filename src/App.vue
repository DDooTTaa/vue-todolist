<template>
  <div id="app">
    <Header />
    <Input />
    <Button />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Input from './components/Input.vue'
import Button from './components/Submit.vue'

export default {
  components: { Header, Input, Button },
  name: 'app', 
  data () {
    return {
    }
  }
}
</script>


<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
