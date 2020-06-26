<template>
  <nav>
    <b-navbar toggleable="sm" variant="light">
      <b-navbar-brand to="/">Yard Sale Tracker</b-navbar-brand>

      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav class="ml-auto">
          <b-nav-item to="/">Home</b-nav-item>
          <b-nav-item v-show="appHasData" to="/app">App</b-nav-item>
          <b-nav-item to="/new-sale">New Yard Sale</b-nav-item>
          <b-nav-item v-show="appHasData" @click="downloadData"
            >Download Data</b-nav-item
          >
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
    <div id="container"></div>
  </nav>
</template>

<script>
export default {
  name: 'Navigation',
  data: function() {
    return {
      appHasData: false
    }
  },
  methods: {
    slugify: function(string) {
      const a =
        'àáâäæãåāăąçćčđďèéêëēėęěğǵḧîïíīįìłḿñńǹňôöòóœøōõőṕŕřßśšşșťțûüùúūǘůűųẃẍÿýžźż·/_,:;'
      const b =
        'aaaaaaaaaacccddeeeeeeeegghiiiiiilmnnnnoooooooooprrsssssttuuuuuuuuuwxyyzzz------'
      const p = new RegExp(a.split('').join('|'), 'g')

      return string
        .toString()
        .toLowerCase()
        .replace(/\s+/g, '-') // Replace spaces with -
        .replace(p, c => b.charAt(a.indexOf(c))) // Replace special characters
        .replace(/&/g, '-and-') // Replace & with 'and'
        .replace(/[^\w\-]+/g, '') // Remove all non-word characters
        .replace(/\-\-+/g, '-') // Replace multiple - with single -
        .replace(/^-+/, '') // Trim - from start of text
        .replace(/-+$/, '') // Trim - from end of text
    },
    downloadData: function() {
      let saleName = JSON.parse(localStorage.getItem('saleName'))
      let categories = JSON.parse(localStorage.getItem('categories'))
      let completedTransactions = JSON.parse(
        localStorage.getItem('completedTransactions')
      )
      let slugName = this.slugify(saleName)
      let downloadObj = {
        saleName,
        categories,
        completedTransactions
      }

      let data =
        'text/json;charset=utf-8,' +
        encodeURIComponent(JSON.stringify(downloadObj))
      let a = document.createElement('a')
      a.href = 'data:' + data
      a.download = `${slugName}.json`
      document.body.appendChild(a)
      a.click()
      document.body.removeChild(a)
    },
    appDataExists: function() {
      if (
        localStorage.saleName &&
        localStorage.categories &&
        localStorage.completedTransactions
      ) {
        console.log('We have data!!!')
        this.appHasData = true
      } else {
        this.appHasData = false
      }
    }
  },
  mounted: function(){
    this.appDataExists()
  },
  watch: {
    $route(to, from) {
      this.appDataExists()
    }
  }
}
</script>

<style lang="scss" scoped>
.navbar-light .navbar-nav .nuxt-link-exact-active {
  color: var(--dark);
  border-bottom: 2px solid var(--secondary);
  padding-bottom: 6px;
}
</style>
