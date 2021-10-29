<template>
  <div class="wrapper">
    <Navbar />
    <main class="content">
      <div class="container">
        <nuxt />
      </div>
    </main>
    <Footer />
  </div>
  
</template>

<script>
  import Navbar from '@/components/Navbar.vue';

  export default {
    components: {
      Navbar
    } 
  }
</script>

<style>
  .wrapper {
    padding-top: 56px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 100vh;
  }
</style>