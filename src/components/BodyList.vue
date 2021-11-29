<template>
 <section class="main">
      <li
        v-for="(item) in todos"
        :key="item.id"
      >
          <h2>{{ item.text }}</h2>
        <Delete/>
        <Update/>
      </li>
  </section>
</template>

<script>
import Delete from "./Delete";
import Update from "./Update";
export default {
  components: {Delete, Update},
  props: {
    todos: { type: Array, default: () => [] }
  }
};
</script>
