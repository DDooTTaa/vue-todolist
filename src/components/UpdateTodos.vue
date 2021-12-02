<template>
  <div>
    <input
      v-show="toggleFlag"
      v-model="str"
      type="text"
      @keypress.enter="updateList"
      @keyup.esc="outInput"
      ref="search"/>
    <button v-show="!toggleFlag" @click="updateBtn()">수정</button>
  </div>
</template>
<script>
export default {
  props: {
    text: {
      type: String,
      default: ''
    },
    index: {
      type: Number,
      default: null
    }
  },
  data() {
    return {
      toggleFlag: false,
      str: '',
      temp: ''
    }
  },
  watch: {
    //watch로 props 를 변경한다.
    text: {
      immediate: true,
      handler(str) {
        this.str = str;
      }
    },
  },
  methods: {
    //버튼과 input 박스를 스위치한다.
    switchToggle() {
      this.toggleFlag = !this.toggleFlag;
    },
    //BodyList 로 str 과 index 보낸다
    updateBtn() {
      this.switchToggle();
      this.temp = this.str;
      this.$refs.search.focus();
    },
    updateList() {
      this.$emit('updateList', this.str, this.index);
      this.switchToggle();
    },
    //ESC 눌렀을 때
    outInput() {
      this.switchToggle();
      this.str = this.temp;
    }
  },
};
</script>
<style scoped>
</style>
