<template>
  <footer>
    <span v-on:click="ClearAll">
      Clear All
    </span>
  </footer>
</template>

<script>
export default {
    name: 'TodoFooter',

    methods: {
      ClearAll() {
        localStorage.clear();
      }
    },
}
</script>

<style scoped>
span {
  cursor: pointer;
}

</style>