<template>
  <div class="budget-list-wrap">
    <ElCard :header="header">
      <template v-if="isEmpty">
        <BudgetListItem :list="list" @deleteItem="onDeleteItem"/>
      </template>
      <ElAlert :closable="false" v-else type="info" :title="emptyTitle"/>
    </ElCard>
  </div>
</template>

<script>
import BudgetListItem from "@/components/BudgetListItem";

export default {
  name: "BudgetList",
  components: {
    BudgetListItem,
  },
  props: {
    list: {
      type: Object,
      default: () => ({})
    },
  },
  data: () => ({
    header: 'Budget List',
    emptyTitle: 'Empty List',
  }),
  computed: {
    isEmpty() {
      return Boolean(Object.keys(this.list).length);
    },
  },
  methods: {
    onDeleteItem(id) {
      this.$emit('deleteItem', id)
    },
  }

}
</script>

<style lang="scss" scoped>
.budget-list-wrap {
  max-width: 500px;
  margin: auto;
}

</style>
