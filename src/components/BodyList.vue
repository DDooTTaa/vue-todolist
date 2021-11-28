<template>
 <section class="main">
      <li
        v-for="({ id, text }, idx) in todos"
        :key="idx"
      >
          <h2>{{ text }}</h2>
      </li>
  </section>
</template>

<script>
export default {
  props: {
    todos: { type: Array, default: () => [] }
  }
};  
</script>