<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo" />
    <span class="addContainer" v-on:click="addTodo">
      <i class="fa-solid fa-plus"></i>
    </span>

    <modal v-if="showModal" @close="showModal = false">
      <h3 slot="header">
        경고!
        <i class="closeModalBtn fa-solid fa-xmark" @click="showModal = false"></i>
      </h3>
      <p slot="body">
        아무것도 입력하지 않으셨습니다.
      </p>
    </modal>
  </div>
</template>

<script>
import Modal from'./common/Modal.vue'

export default {
    name: 'TodoInput',

    data() {
      return {
        newTodoItem: "",
        showModal: false
      }
    },
    methods: {
      addTodo() {
        if (this.newTodoItem !== '') {
        // this.$emit('addTodoItem', this.newTodoItem);
        this.$store.commit('addOneItem', this.newTodoItem);
        this.clearInput();
        } else {
          this.showModal = !this.showModal
        }
      },
      clearInput() {
        this.newTodoItem = '';
      }
    },
    components: {
      Modal,
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