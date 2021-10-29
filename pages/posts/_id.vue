<template>
  <section class="post"> 
    <div class="card mt-5">
      <div class="card-body">
        <h5 class="card-title">{{post.id}}). {{post.title}}</h5>
        <p class="card-text">{{post.body}}</p>
        
      </div>
    </div>
    <nuxt-link to="/posts">All posts</nuxt-link>
  </section>
</template>

<script>
export default {
  
  loading: true,

  async asyncData ({$axios, params}) {

    const post = await $axios.$get(`https://jsonplaceholder.typicode.com/posts/${params.id}`);
    console.log(post)
    return { post }
 
  },

  data: () => ({
    post: {}
  }),

  head() {
    return {
      title: this.post.title + " | NuxtJs",
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Home page description'
        }
      ]
    }
  },

  mounted() {
    this.$nextTick(() => {
      this.$nuxt.$loading.start()
      setTimeout(() => this.$nuxt.$loading.finish(), 1000)
    })
  }

}
</script>