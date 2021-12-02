<template>
  <div>
    <li class="lists__item item">
      <h3 class="item__title">{{ todo.title }}</h3>
      <mySwitch />
    </li>
  </div>
</template>

<script>
import mySwitch from "./v-switch.vue";
export default {
  name: "todo-item",
  components: {
    mySwitch,
  },
};
</script>

<style></style>
