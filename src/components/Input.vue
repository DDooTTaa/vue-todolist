<template>
<div>
    <input type="text" v-model="input"/>
    <button type="button" @click="getData">Submit</button>
    <button type="button" @click="setData">Set</button>
</div>
</template>

<script>
export default{
    data () {
        return {
            input: "dd",
        };
    },
    methods: {
        getData() {
            alert(this.input);
        },
        setData() {
            this.input = "12345"
        }
    }
}
</script>

<style scoped>
button {
    color: tomato;
    font-weight: 600;
}
</style>