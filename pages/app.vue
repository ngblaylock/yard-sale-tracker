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
            :style="
              `background-color: ${categories[transaction.category].color};`
            "
          ></div>
          ${{ Number.parseFloat(transaction.price).toFixed(2) }}
          <div class="text-danger ml-auto p-3">
            <i class="fas fa-trash"></i>
          </div>
        </div>

        <form>
          <div class="d-flex align-items-center mt-3 category-select">
            <b-dropdown id="dropdown-1" class="category-select mx-3" no-caret>
              <template v-slot:button-content>
                <i class="fas fa-plus"></i>
              </template>
              <div class="py-2 px-3 d-flex flex-wrap justify-content-between">
                <button
                  class="category-option"
                  :style="`background-color: ${category.color}`"
                  v-for="(category, index) in categories"
                  :key="index"
                  @click.prevent=""
                ></button>
              </div>
            </b-dropdown>
            <div class="input-group">
              <div class="input-group-prepend">
                <span class="input-group-text rounded-left">$</span>
              </div>
              <input
                type="number"
                class="form-control rounded-right"
                aria-label="Amount (to the nearest dollar)"
              />
            </div>
            <button class="btn btn-link"><i class="fas fa-times"></i></button>
          </div>
          <button class="btn btn-light mt-3" type="submit">Add Item</button>
        </form>
        <hr class="double-line" />
        <p class="h2 text-right">
          <small class="text-secondary">Transaction Total:</small> ${{Number.parseFloat(transactionTotal).toFixed(2)}}
        </p>
        <p class="text-right">
          <button class="btn btn-light">Save and Clear</button>
        </p>
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
        }
      ]
    }
  },
  computed: {
    transactionTotal: function() {
      return this.thisTransaction.reduce((currentTotal, transaction) => {
        return currentTotal + parseFloat(transaction.price)
      }, 0)
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
hr.double-line {
  border-top: 3px double var(--secondary);
}
</style>

<style lang="scss">
.category-select {
  .dropdown-toggle-no-caret {
    border-radius: 20px;
  }
  .category-option {
    display: inline-block;
    width: 32px;
    height: 32px;
    background-color: green;
    margin: 0.25em;
    border-radius: 32px;
  }
}
</style>
