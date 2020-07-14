<template>
  <div id="page-content">
    <!-- <div class="alert alert-warning text-center mb-0 rounded-0">This app is currently in development. There are several known issues and features not yet implemented. Use this app at your own risk.</div> -->
    <NavBar />
    <main>
      <nuxt />
    </main>
    <FooterBar />
  </div>
</template>

<script>
export default {
  name: "DefaultLayout"
}
</script>

<style lang="scss">
  #page-content{
    display: flex;
    flex-direction: column;
    min-height: 100vh;
    main{
      flex: 1 1 auto;
      display: flex;
      flex-direction: column;
    }
    .container{
      max-width: 1170px;
    }
  }
</style>