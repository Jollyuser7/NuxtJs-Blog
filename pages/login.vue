<template>
  <section class="login">
    <div v-if="$route.query.message" class="alert alert-danger mb-3">
      Need login first
    </div>
    <h1>Login</h1>
    <form @submit.prevent="onSubmit">

      <div class="mb-3">
        <label for="exampleInputEmail1" class="form-label">Email address</label>
        <input type="text" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp">
        <div id="emailHelp" class="form-text">We'll never share your email with anyone else.</div>
      </div>

      <div class="mb-3">
        <label for="exampleInputPassword1" class="form-label">Password</label>
        <input type="password" class="form-control" id="exampleInputPassword1">
      </div>

      <div class="mb-3 form-check">
        <input type="checkbox" class="form-check-input" id="exampleCheck1">
        <label class="form-check-label" for="exampleCheck1">Check me out</label>
      </div>

      <button type="submit" class="btn btn-primary">Submit</button>

    </form>
    <nuxt-link class="link-primary mt-3 d-inline-block" to="/">
      Go to home
    </nuxt-link>
  </section>
</template>

<script>
  export default {
    layout: 'login',

    methods: {
      onSubmit() {
        this.$store.dispatch('login');
        this.$router.push('/')
      },
    }
  }
</script>

<style>
  .login {
    max-width: 400px;
    margin: 0 auto;
  }
</style>


