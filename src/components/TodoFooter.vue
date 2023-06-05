<template>
  <footer>
    <span v-on:click="clearTodo">
      Clear All
    </span>
  </footer>
</template>

<script>
import { mapMutations } from 'vuex';

export default {
    name: 'TodoFooter',

    methods: {
      ...mapMutations({
        clearTodo : 'clearAllItems'
      })    
  }
}
</script>

<style scoped>
span {
  cursor: pointer;
}

</style>