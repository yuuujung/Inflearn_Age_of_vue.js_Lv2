<template>
  <div>
    <ul>
      <li v-for="(todoItem, index) in this.storedTodoItems" v-bind:key="todoItem.item" class="shadow">
        <span class="checkBtn" v-on:click="toggleComplete({todoItem, index})">
          <i class="fa-solid fa-check"></i>
        </span>
        <span v-bind:class="{textCompleted: todoItem.completed}">
        {{ todoItem.item }} 
        </span>
        <span v-on:click="removeTodo({todoItem, index})" class="removeBtn">
          <i class="fa-solid fa-trash"></i>
        </span>
      </li>
    </ul>
  </div>
</template>

<script>
import { mapGetters, mapMutations } from 'vuex';

export default {
    name: 'TodoList', 

    methods: {
      ...mapMutations({
        removeTodo: 'removeOneItem',
        toggleComplete: 'toggleOneItem',
      }),

      // removeTodo(todoItem, index) {
      //   this.$store.commit('removeOneItem', {todoItem, index});
      // },
      // toggleComplete(todoItem, index) {
      // this.$store.commit('toggleOneItem', {todoItem, index});
      // },
    },

    computed: {
      // todoItems() {
      //   return this.$store.getters.storedTodoItems
      // },
      ...mapGetters({
        storedTodoItems: 'getTodoItems'
      })
    },

    // created() {
    //   if (localStorage.length > 0) {
    //     for (var i = 0; i < localStorage.length; i++) {
    //       this.todoItems.push(JSON.parse(localStorage.getItem(localStorage.key(i))));
    //     }
    //   }
    // }

}
</script>

<style scoped>
ul {
  text-align: left;
  padding-left: 0px;
  margin: 0 auto;
  width: 500px;
}
ul li {
    display: flex;
    justify-content: center;
    min-height: 50px;
    height: 50px;
    line-height: 50px;
    margin: 0.5rem 0;
    padding: 0 0.9rem;
    background: white;
    list-style: none;
    border-radius: 5px;
}
.textCompleted {
    text-decoration: line-through;
    color: #b3adad;
}

.removeBtn {
  color: red;
  margin-left: auto;
  cursor: pointer;
}

.checkBtn {
  margin-right: 10px;
  cursor: pointer;
}
</style>