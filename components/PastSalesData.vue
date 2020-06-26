<template>
  <b-card no-body class="mb-1">
    <b-card-header header-tag="header" class="p-0 bg-white" role="tab">
      <b-button
        block
        v-b-toggle.accordion-1
        variant="link"
        class="text-left text-dark text-decoration-none d-flex align-items-center"
        ><span>$17.50 <small class="text-secondary">7 items sold</small></span>
        <i class="fas fa-caret-down text-secondary ml-auto"></i
      ></b-button>
    </b-card-header>
    <b-collapse
      id="accordion-1"
      visible
      accordion="my-accordion"
      role="tabpanel"
    >
      <b-card-body class="px-3 pb-3 pt-1">
        <div class="d-flex flex-wrap">
          <div class="d-flex align-items-center mr-3" v-for="(x, index) in 7" :key="index">
            <div class="category-color mr-2" style="background-color: blue"></div>
            <div>${{x}}.50 ({{index}})</div>
          </div>
        </div>
      </b-card-body>
    </b-collapse>
  </b-card>
</template>

<script>
export default {
  data: function() {
    return {
      text: 'this is basic text'
    }
  }
}
</script>

<style scoped lang="scss">
.card::v-deep {
  .card-header {
    border-bottom: 0;
    border-radius: calc(0.25rem - 1px);
    button {
      border-radius: 3px;
      &.not-collapsed i{
        transform: rotate(180deg);
      }
    }
  }
  .card-body{
    .category-color{
      width: 1em;
      height: 1em;
      border-radius: 100%;
    }
  }
}
</style>
