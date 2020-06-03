<template>
  <nav>
      <b-navbar toggleable="sm" variant="light">
        <b-navbar-brand href="#">NavBar</b-navbar-brand>
    
        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
    
        <b-collapse id="nav-collapse" is-nav>
          <b-navbar-nav class="ml-auto">
            <b-nav-item href="#">*New Yard Sale</b-nav-item>
            <b-nav-item href="#">*Save Data</b-nav-item>
            <b-nav-item href="#">*Upload Data</b-nav-item>
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
