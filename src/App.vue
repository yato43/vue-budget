<template>
<div id="app">
  <BudgetList :list="list" />
</div>
</template>

<script>

import BudgetList from "@/components/BudgetList.vue";

export default {
  name: 'App',
  components: {
    BudgetList,
  },
  data: () => ({
    list: {
      1: {
        type: 'INCOME',
        value: 100,
        comment: 'Some comments',
        id: 1,
      },
      2: {
        type: 'OUTCOME',
        value: -50,
        comment: 'Some outcome comments',
        id: 2,
      },
    },
  }),
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
