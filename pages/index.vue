<template>
  <section class="section">
    <div class="tile is-ancestor">
      <a :href="authUrl()">
        <button class="button is-primary">Авторизоваться</button>
      </a>
    </div>

    <div class="tile is-ancestor" style="flex-wrap: wrap;">

      <UserCard
        class="tile is-4 is-child"
        v-for="friend in friends"
        :key="friend.id"
        :first-name="friend.first_name"
        :last-name="friend.last_name"
        :bdate="friend.bdate"
        :sex="friend.sex === 1 ? 'женский' : 'мужской'"
        :country="friend.country ? friend.country.title : 'страна не указана'"
        :city="friend.city ? friend.city.title : 'город не указан'"
        :photo="friend.photo_id"
        :has-photo="friend.has_photo == 1"
      >
      </UserCard>

    </div>
  </section>
</template>

<script>
import { getAccess, getUrlAuth, getParamsObj, getFriends } from '~/assets/vkapi.js'
import { getData } from '~/assets/storage.js'
import UserCard from '~/components/UserCard'

export default {
  name: 'HomePage',
  components: {
    UserCard
  },
  data() {
      return {
        friends: null
      }
  },
  methods: {
    authUrl () {
      return getUrlAuth(process.env.VKAPP_ID)
    },
    async loadFriends () {
      try {
        let { user_id, access_token } = getData()
        if (!user_id || !access_token) throw('')

        let data = await getFriends(user_id, access_token)

        if (data === null) throw('Неправильные параметры запроса!')
        if (data['error']) throw('Ошибка авторизации!')
        this.friends = data

      } catch (err) {
        console.error(err)
        this.friends = null
      }
    },
  },
  mounted () {
    this.loadFriends ()
  }
}
</script>

