<template>
  <div class="todo__form">
    <form @submit.prevent="onSubmit" method="">
      <h2 class="title">Add todo</h2>
      <input
        class="input"
        type="text"
        placeholder="Todo name"
        name="addTodo"
        v-model="title"
      />
      <v-button />
    </form>
  </div>
</template>

<script>
import vButton from "./v-button.vue";
export default {
  name: "todo-form",
  components: {
    vButton,
  },
  data() {
    return {
      title: "",
    };
  },
  methods: {
    onSubmit() {
      this.$emit("addTodo", this.title);
      this.title = "";
    },
  },
};
</script>

<style lang="scss" scoped>
.todo__form {
  width: 518px;
  height: 171px;
  //display: flex;
  background: var(--color-grey);
  // border: 2px solid green;
  border-radius: var(--radius);
  @media only screen and (max-width: 649px) {
    width: 100%;
  }
}

form {
  position: relative;
  padding: 32px 29px 31px 33px;

  @media only screen and (max-width: 768px) {
    padding-left: 23px;
    padding-right: 23px;
  }
}

.input {
  width: 100%;
  padding: 18px;
  border-radius: 6px;
  font-size: 16px;
  border: none;
}
.btn {
  width: 46px;
  height: 41px;
  border-radius: 6px;
  top: 96px;
  right: 50px;
  background: var(--color-acsent);
  color: #fff;
  position: absolute;
  border: none;
  @media only screen and (max-width: 768px) {
    right: 30px;
  }
}
</style>
