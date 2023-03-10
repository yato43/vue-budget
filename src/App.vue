<template>
  <div id="app">
    <FormMain @submitForm="onSubmit"/>
    <TotalBalance :total="totalBalance"/>
    <BudgetList :list="list" @deleteItem="onDeleteItem"/>
  </div>
</template>

<script>

import BudgetList from "@/components/BudgetList.vue";
import TotalBalance from "@/components/TotalBalance";
import FormMain from "@/components/FormMain";

export default {
  name: 'App',
  components: {
    BudgetList,
    TotalBalance,
    FormMain,
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
  computed: {
    totalBalance() {
      return Object.values(this.list).reduce((acc, item) => acc + item.value, 0)
    },
  },
  methods: {
    onDeleteItem(id) {
      console.log(1)
      delete this.list[id]
    },
    onSubmit(data){
      const newObj = {
        ...data,
        id: String(Math.random())
      };
      this.list[newObj.id] = newObj;
    },
  },
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
