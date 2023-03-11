<template>
  <div class="total-value" :class="balanceObj">
    Balance: {{ total }}
  </div>
</template>

<script>
export default {
  name: "TotalBalance",
  props: {
    total: {
      type: Number,
      default: 0,
    },
  },
  computed: {
    balanceObj() {
      let sign = 'neutral';
      if (this.total > 0) {
        sign = 'positive'
      } else if (this.total < 0) {
        sign = 'negative'
      }
      return sign
    }
  },
}
</script>

<style scoped>
.total-value {
  font-size: 26px;
  text-transform: uppercase;
  padding: 20px;
  text-align: center;
}

.positive {
  color: #05f618;
}

.negative {
  color: #f00;
}

.neutral {
  color: #000;
}

</style>
