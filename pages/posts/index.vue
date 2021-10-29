<template>
  <section class="posts">

    <h1>Post</h1>

    <div v-for="post of posts" :key="post.id" class="row">
      <div class="col-sm-10 mb-3">
        <div class="card">
          <div class="card-body">
            <h5 class="card-title">
              <nuxt-link :to="`/posts/${post.id}`" class="link-secondary">{{post.title}}</nuxt-link>
            </h5>
            <p class="card-text">{{post.id}}). {{post.body}}</p>
            <nuxt-link :to="`/posts/${post.id}`" class="btn btn-primary">Читать</nuxt-link>
          </div>
        </div>
      </div>
    </div>
   
  </section>
</template>

<script>
export default {

  data: () => ({
    title: 'All posts | NuxtJs',
    // posts: []
  }),

  head() {
    return {
      title: this.title,
      meta: [
        {name: 'keywords', content: 'Vue.js, Nuxt.js, js'},
        {name: 'description', content: 'Learn Nuxt.js framework'}
      ]
    }
  },

  validate({route}) {
    // console.log(route);
    return true
  },

  async asyncData({$axios}) {
    const posts = await $axios.$get('https://jsonplaceholder.typicode.com/posts');
    // const posts = postsList.slice(0, 5)
    return {posts}
  },

  

  beforeCreate() {
    console.log("Страница еще не готова")
  },

  created() {
    console.log("Страница уже готова")
  },

  fetch() {
    console.log("Здесь выполняем асинхронный запрос")
  },
  
  mounted() {
    console.log("Страница смонтирована")
  }

}
</script>