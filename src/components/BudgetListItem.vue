<template>
  <div class="list-item" v-for="(item, prop) in list" :key="prop">
    <span class="budget-comment">{{item.comment}}</span>
    <span class="budget-value">{{item.value}}</span>
    <ElButton type="danger" size="small" @click="deleteItem(item.id)">Delete</ElButton>
  </div>
</template>

<script>
export default {
  name: "BudgetListItem",
  props: {
    list: {
      type: Object,
      default: () => ({})
    },
  },
  methods: {
    deleteItem(id) {
      this.$emit('deleteItem', id)
    },
  },
}
</script>

<style  lang="scss" scoped>
.list-item {
  display: flex;
  align-items: center;
  padding: 10px 15px;

.budget-value {
  font-weight: bold;
  margin-left: auto;
  margin-right: 20px;
}

}
</style>
