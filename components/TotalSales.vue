<template>
  <div class="card">
    <div class="card-header bg-dark text-white text-center">
      <p class="h4">
        Total Sales
      </p>
      <p class="h1">${{totalSales | toPrice}}</p>
    </div>
    <div class="card-body bg-light pb-0">
      <div
        v-for="(category, index) in categories"
        :key="index"
        class="d-flex mb-3 align-items-center"
      >
        <div
          class="mr-2 rounded-circle"
          :style="`background-color: ${category.color}`"
          style="width: 3em; height: 3em;"
        ></div>
        <div>
          <p class="mb-0" style="font-size: 1.8em;">
            ${{ categorizedTransactionTotals[index].amount | toPrice }}
            <small class="text-muted"
              >{{ categorizedTransactionTotals[index].quantity }} items
              sold</small
            >
          </p>
          <p class="mb-0">
            <strong>{{ category.name }}</strong>
          </p>
        </div>
      </div>
    </div>
    <div class="card-body bg-light border-top">
      <h2>Past Transactions</h2>
      <div role="tablist">
          <PastSalesData />
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TotalSales',
  props: ['categories', 'completedTransactions'],
  computed: {
    categorizedTransactionTotals: function() {
      let transformed = []
      for (var i = 0; i < this.categories.length; i++) {
        transformed.push({ amount: 0, quantity: 0 })
      }
      this.completedTransactions.forEach(transaction => {
        transaction.forEach(t => {
          transformed[t.category].amount += parseFloat(t.price)
          transformed[t.category].quantity++
        })
      })
      return transformed
    },
    totalSales: function() {
      return this.categorizedTransactionTotals.reduce((currentTotal, i) => {
        return currentTotal + i.amount
      }, 0)
    }
  },
  filters: {
    toPrice: function(value) {
      if (!value) return '0.00'
      return value.toFixed(2)
    }
  }
}
</script>
