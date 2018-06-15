<template>
    <section class="section">
        <h1>Завершение авторизации...</h1>
    </section>
</template>

<script>
import { getParamsObj } from '~/assets/vkapi.js'
import { storeData } from '~/assets/storage.js'

export default {
  name: 'AuthPage',
  data() {
      return {
      }
  },
  methods: {
  },
  mounted () {
    try {
      let fullUrl = window.location.href

      let params = getParamsObj(fullUrl)
      if (!params['user_id'] || !params['access_token']) {
        throw('Нет данных авторизации!')
      }

      let user_id = params['user_id']
      let access_token = params['access_token']
      storeData(user_id, access_token)

    } catch (err) {
      console.error(err)
    }
    // window.location.href = '/'
    window.location.href = 'https://darchansuleimenov.github.io/nuxt-vk/'
    // this.$router.go('/')
  }
}
</script>

