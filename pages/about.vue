<template>
  <section class="about">
    <h1>About page</h1>
    <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Obcaecati quae doloribus numquam earum rerum inventore asperiores delectus eligendi, perferendis esse nemo. Optio dolor doloribus dignissimos corrupti, velit explicabo officia incidunt.</p>
    <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Consectetur cum, mollitia, consequatur laudantium quibusdam totam repudiandae aliquid aut vel voluptatum aliquam optio explicabo similique, delectus libero perferendis esse nulla quo.</p>
    <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Nemo, architecto sit nam aliquid illo maxime exercitationem vel, repellendus quo odit necessitatibus neque excepturi, eius iure minus blanditiis eligendi nisi iste.</p>
  </section>
</template>


<script>
export default {
  middleware: ['auth']
}
</script>

<style lang="css">
  .about {
    min-height: 1000px
  }
</style>