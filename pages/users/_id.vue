<template>
  <section>
    <h1>{{user.name}}</h1>
    <!-- <p>Phone: {{name.phone}}</p> -->
  </section>
</template>

<script>
  export default {

    async asyncData({$axios, params}) {
      const user = await $axios.$get(`https://jsonplaceholder.typicode.com/users/${params.id}`);
      console.log(user)
      return {user}
    },

    // validate({params}) {
    //   return /^\d+$/.test(params.id)
    // }
  }
</script>