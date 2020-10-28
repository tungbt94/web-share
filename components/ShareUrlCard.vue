<template>
  <v-card>
    <v-card-title> Share URL or text </v-card-title>
    <v-card-subtitle>
      {{ message }}
    </v-card-subtitle>
    <v-card-text>
      <pre>
        title: 'Demo',
        text: 'Check out new Hoodies and sweatshirts',
        url:
          'https://demo.vuestorefront.io/women/tops-women/hoodies-and-sweatshirts-women.html',
      </pre>
    </v-card-text>
    <v-card-actions>
      <v-btn color="blue" @click="share">Share</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  name: 'ShareUrlCard',

  data() {
    return {
      message: '',
    }
  },

  mounted() {
    if (navigator.share) {
      this.message = 'exists navigator.share'
    } else {
      this.message = 'not exists navigator.share'
    }
  },

  methods: {
    async share() {
      if (navigator.share) {
        this.message = 'exists navigator.share'
        try {
          await navigator.share({
            title: 'Demo',
            text: 'Check out new Hoodies and sweatshirts',
            url:
              'https://demo.vuestorefront.io/women/tops-women/hoodies-and-sweatshirts-women.html',
          })
          this.message = 'Successful share'
        } catch (error) {
          this.message = error.message
        }
      }
      this.message = 'not exists navigator.share'
    },
  },
}
</script>
