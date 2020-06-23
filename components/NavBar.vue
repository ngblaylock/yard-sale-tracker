<template>
  <nav>
      <b-navbar toggleable="sm" variant="light">
        <b-navbar-brand to="/">Yard Sale Tracker</b-navbar-brand>
    
        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
    
        <b-collapse id="nav-collapse" is-nav>
          <b-navbar-nav class="ml-auto">
            <b-nav-item to="/app">App</b-nav-item>
            <b-nav-item to="/new-sale">New Yard Sale</b-nav-item>
            <b-nav-item to="/">*Download Data</b-nav-item>
            <b-nav-item to="/">*Upload Data</b-nav-item>
          </b-navbar-nav>
    
        </b-collapse>
      </b-navbar>
  </nav>
</template>

<script>
export default {
  name: 'Navigation'
}
</script>

<style lang="scss" scoped>
  .navbar-light .navbar-nav .nuxt-link-exact-active{
    color: var(--dark);
    border-bottom: 2px solid var(--secondary);
    padding-bottom: 6px;
  }
</style>
