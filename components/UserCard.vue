<template>
  <div class="card">
    <div class="card-content">
      <div class="media">
        <div class="media-left">
          <figure class="image is-128x128">
            <img v-if="hasPhoto" :src="photo" alt="Placeholder image">
            <img v-else src="https://bulma.io/images/placeholders/128x128.png" alt="Placeholder image">
          </figure>
        </div>
        <div class="media-content">
          <p class="title is-4">{{ firstName }}</p>
          <p class="subtitle is-6">{{ lastName }}</p>
          <p class="subtitle is-6">{{ sex }}</p>
          <p class="subtitle is-6">{{ bdate }}</p>
          <p class="subtitle is-6">{{ country }}</p>
          <p class="subtitle is-6">{{ city }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    firstName: {
      type: String,
      default: 'имя неизвестно'
    },
    lastName: {
      type: String,
      default: 'фамилия неизвестна'
    },
    photo: {
      type: String,
      default: 'https://bulma.io/images/placeholders/128x128.png'
    },
    bdate: {
      type: String,
      default: 'дата рождения неизвестна'
    },
    sex: {
      type: String,
      default: 'пол неизвестен'
    },
    country: {
      type: String,
      default: 'страна неизвестна'
    },
    city: {
      type: String,
      default: 'город неизвестен'
    },
    hasPhoto: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
    }
  }
}
</script>
