<template>
  <section>
    <h1>Users Page</h1>
    <ul class="list-group">
      <li v-for="user of users" :key="user.id">
        <h6>User {{user.name}}</h6>  
        <nuxt-link :to="`/users/${user.id}`" class="btn btn-primary">Читать</nuxt-link>
      </li>
    </ul>
  </section>
</template>

<script>
export default {

  async fetch({store}) {
    if(store.getters['users/users'].length === 0) {
      await store.dispatch('users/fetch')
    }
  },

  data: () => ({
    // users: []
  }),

  computed: {
    users() {
      return this.$store.getters['users/users']
    }
  }
}
</script>

<style>
  .list-group {
    list-style: none
  }
</style>