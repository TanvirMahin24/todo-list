<template>
  <div class="card" v-bind:class="[data.important ? 'bgImp' : '']">
    <i
      @click="importantTodo(data.id)"
      v-bind:class="[data.important ? 'important' : '']"
      class="fas fa-crown"
    ></i>
    <h3 v-bind:class="[data.completed ? 'through' : '']">
      {{ data.name }}
      <i
        v-bind:class="[data.completed ? 'done' : '']"
        class="fas fa-check-square"
        @click="doneTodo(data.id)"
      ></i>
    </h3>
    <i @click="deleteTodo(data.id)" class="fas fa-trash-alt"></i>
  </div>
</template>
<script>
export default {
  name: "Todo",

  props: {
    data: Object,
  },
  methods: {
    deleteTodo(id) {
      this.$emit("deleteTodoEvent", id);
    },
    importantTodo(id) {
      this.$emit("makeImportantEvent", id);
    },
    doneTodo(id) {
      this.$emit("todoDoneEvent", id);
    },
  },
};
</script>

<style scoped>
.through {
  text-decoration: line-through;
  font-weight: 200;
}
.card {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 600px;
  height: 140px;
  margin-bottom: 10px;
  border-radius: 10px;
  box-shadow: 2px 2px 3px rgba(0, 0, 0, 0.5);
  background: #fff;
  color: #101e2c;
}
.bgImp {
  background: rgb(202, 210, 255);
}
.fa-crown {
  color: rgba(39, 38, 1, 0.349);
}
.fa-trash-alt {
  cursor: pointer;
  color: rgb(160, 1, 1);
  font-size: 1.3rem;
}
.fa-crown.important {
  color: rgb(228, 224, 23);
}
.fa-check-square {
  color: #101e2c31;
  font-size: 1.5rem;
}
.fa-check-square.done {
  color: #003a74;
}
</style>
