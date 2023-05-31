<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo" />
    <span class="addContainer" v-on:click="addTodo">
      <i class="fa-solid fa-plus"></i>
    </span>
  </div>
</template>

<script>
export default {
    name: 'TodoInput',
    data() {
      return {
        newTodoItem: "",
      }
    },
    methods: {
      addTodo() {
        if (this.newTodoItem !== '') {
        var obj = {completed: false, item: this.newTodoItem};
        localStorage.setItem(this.newTodoItem, JSON.stringify(obj));
        this.clearTodo()
        }
      },
      clearTodo() {
        this.newTodoItem = '';
      }
    }

}
</script>

<style scoped>
input {
  min-height: 50px;
    height: 50px;
    line-height: 50px;
    margin: 0.5rem 0;
    padding: 0 0.9rem;
    background: white;
    border-radius: 5px;
}
.addContainer {
  cursor: pointer;
  margin-left: 5px;
}

</style>