<template>
  <footer class="bg-secondary text-white p-3">
    <div class="d-flex justify-content-center">
        <div class="p-2"><a href="https://nathanblaylock.com" target="_blank"><i class="fas fa-copyright"></i> Nathan Blaylock, {{ new Date().getFullYear() }}</a></div>
        <div class="p-2"><a href="#"><i class="far fa-comment"></i> *Feedback & Bugs</a></div>
        <div class="p-2"><a href="https://www.paypal.me/NathanBlaylock" target="_blank"><i class="fas fa-donate"></i> Donate</a></div>
    </div>
  </footer>
</template>

<script>
export default {
  name: "FooterBar"
}
</script>

<style lang="scss" scoped>
  a{
    color: var(--light);
    padding: 15px;
    border-radius: 6px;
    transition: all .2s;
    &:hover{
      background-color: rgba(0, 0, 0, 0.2);
      text-decoration: none;
    }
  }
</style>
