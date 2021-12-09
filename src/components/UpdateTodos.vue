<template>
  <div>
    <input
      type="text" v-model="str" @keyup.enter="updateList" @keyup.esc="outInputBox" v-show="toggleFlag"
    />
    <button v-show="!toggleFlag" @click="updateBtn">수정</button>
  </div>
</template>

<script>
export default {
  props: {
    text: String,
    index: Number,
  },
  data() {
    return {
      toggleFlag: false,
      str: this.text,
      temp: '',
    };
  },
  methods: {
    //버튼과 input 박스를 스위치한다.
    switchToggle() {
      this.toggleFlag = !this.toggleFlag;
    },
    //버튼이 눌렸을 때 input 박스가 나오도록 하고 빈 스트링에 현재 스트링 저장
    updateBtn() {
      this.switchToggle();
      this.temp = this.str;
    },
    //엔터를 누르면 BodyList 로 str 과 index 를 보낸다
    updateList() {
      this.$emit('update', this.str, this.index);
      this.switchToggle();
    },
    //ESC 버튼을 눌렀을 때 이전 입력값을 가져온다.
    outInputBox() {
      this.switchToggle();
      this.str = this.temp;
    },
  },
};
</script>

<style scoped>
</style>
