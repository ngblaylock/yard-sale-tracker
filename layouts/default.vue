<template>
  <div id="page-content">
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
    }
    .container{
      max-width: 1170px;
    }
  }
</style>