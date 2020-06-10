<template>
  <div class="inputCard">
    <input
      @keyup.enter="addTodo"
      v-model="input"
      type="text"
      class="input"
      placeholder="Add the name of the todo"
    />
  </div>
</template>

<script>
export default {
  name: "AddTodo",
  props: {
    msg: String,
  },
  data() {
    return {
      input: "",
    };
  },
  methods: {
    addTodo() {
      this.$emit("addTodoEvent", this.input);
      this.input = "";
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.inputCard {
  margin: 10px 0;
  padding: 0 30px;
  color: #101e2c;
}
.input {
  width: 300px;
  height: 30px;
  background: none;
  outline: none;
  border: none;
  border-bottom: 2px solid #fff;
  text-align: center;
  font-size: 1.2rem;
  color: #fff;
}
input::placeholder {
  color: #101e2c;
}
.input:focus {
  border-bottom: 2px solid #101e2c;
}
</style>
