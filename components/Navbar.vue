<template>
  <nav class="navbar fixed-top navbar-expand-lg navbar-light bg-light">
    <div class="container-fluid">
      <a class="navbar-brand" href="/">Blog</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">

          <li class="nav-item">
            <nuxt-link exact no-prefetch active-class="active" to="/" class="nav-link" aria-current="page">Home</nuxt-link>
          </li>

          <li class="nav-item">
            <nuxt-link active-class="active" class="nav-link" to="/about">About</nuxt-link>
          </li>

          <li class="nav-item">
            <nuxt-link active-class="active" class="nav-link" to="/posts">Posts</nuxt-link>
          </li>

          <li class="nav-item">
            <nuxt-link active-class="active" class="nav-link" to="/users">Users</nuxt-link>
          </li>
          
          <li class="nav-item" v-if="!hasToken">
            <nuxt-link active-class="active" class="nav-link" to="login">Login</nuxt-link>
          </li>

          <li class="nav-item" v-else>
            <a href="#" @click.prevent="logOut" active-class="active" class="nav-link">Logout</a>
          </li>

        </ul>
      </div>

    </div>
  </nav>
</template>

<script>
export default {
  computed: {
    hasToken() {
      return this.$store.getters.hasToken
    }
  },
  methods: {
    logOut() {
      this.$store.dispatch('logout');
      this.$router.push('/')
    }
  }
}
</script>