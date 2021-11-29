<template>
 <section class="main">
      <li
        v-for="(item) in todos"
        :key="item.id"
      >
          <h2>{{ item.text }}</h2>
        <Delete/>
      </li>
  </section>
</template>

<script>
import Delete from "./Delete";
export default {
  components: {Delete},
  props: {
    todos: { type: Array, default: () => [] }
  }
};
</script>
