<template>
  <input
    type="checkbox"
    :checked="checked"
    class="item__checkbox--switch-on"
    @change="changed()"
  />
</template>

<script>
export default {
  model: {
    prop: "checked",
    event: "change",
  },
  methods: {
    changed() {
      this.completed = !this.completed;
      console.log(this.completed);
    },
  },
  props: {
    checked: Boolean,
  },
};
</script>

<style></style>
