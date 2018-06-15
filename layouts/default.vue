<template>
  <div>
    <section class="hero">
      <div class="hero-body">
        <div class="container">
          <h1 class="title">
            nuxt-vk
          </h1>
          <h2 class="subtitle">
            nuxtjs, buefy, axios, vk api
          </h2>
        </div>
      </div>
    </section>

    <section class="main-content columns">

      <div class="container column is-12">
        <nuxt />
      </div>

    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        { title: 'Home', icon: 'home', to: { name: 'index' } },
        { title: 'Inspire', icon: 'lightbulb', to: { name: 'inspire' } }
      ]
    }
  }
}
</script>
