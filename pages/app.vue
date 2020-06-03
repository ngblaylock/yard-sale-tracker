<template>
  <div class="container mt-4">
    <div class="row">
      <div class="col-sm-7">
        <h1>This Transaction</h1>
        <div
          class="transaction"
          v-for="(transaction, index) in thisTransaction"
          :key="index"
        >
          <div
            class="color"
            :style="`background-color: ${categories[transaction.category].color};`"
          ></div>
          ${{ Number.parseFloat(transaction.price).toFixed(2) }}
          <div class="text-danger ml-auto"><i class="fas fa-trash"></i></div>
        </div>
      </div>
      <div class="col-sm-5">
        <TotalSales />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      thisTransaction: [
        {
          category: 0,
          price: '12'
        },
        {
          category: 0,
          price: '1'
        },
        {
          category: 1,
          price: '19'
        },
        {
          category: 2,
          price: '2.5'
        },
        {
          category: 3,
          price: '13.75'
        }
      ],
      categories: [
        {
          name: 'Blue',
          color: '#1C7CD5'
        },
        {
          name: 'Green',
          color: '#5CB85C'
        },
        {
          name: 'Yellow',
          color: '#F0AD4E'
        },
        {
          name: 'Red',
          color: '#D9534F'
        },
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
.transaction {
  font-size: 18px;
  display: flex;
  align-items: center;
  &:nth-child(even) {
    background-color: var(--light);
  }
  .color {
    width: 32px;
    height: 32px;
    border-radius: 32px;
    margin: 12px;
  }
}
</style>
