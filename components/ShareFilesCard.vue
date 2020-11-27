<template>
  <v-card>
    <v-card-title>Share files</v-card-title>
    <v-card-subtitle>
      {{ message }}
    </v-card-subtitle>
    <v-card-text>
      <pre>
        title: 'Demo share files',
        text: 'Screenshots'
      </pre>
      <v-file-input show-size label="File input" @change="changeFile" />
    </v-card-text>
    <v-card-actions>
      <v-btn color="blue" @click="share">Share</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  name: 'ShareFilesCard',

  data() {
    return {
      message: '',
      file: [],
    }
  },

  mounted() {
    if (navigator.canShare) {
      this.message = 'navigator.canShare'
    } else {
      this.message = 'navigator.canShare === false'
    }
  },

  methods: {
    async shareFile() {
      const files = Object.freeze([this.file]) // share API require frozen array
      const canShare = navigator.canShare && navigator.canShare({ files })
      if (canShare) {
        this.message = 'navigator.canShare'
        try {
          await navigator.share({
            files,
            title: 'Demo share files',
            text: 'Screenshots',
          })
          this.message = 'Successful share'
        } catch (error) {
          this.message = error.message
        }
      }
      this.message = 'navigator.canShare === false'
    },

    changeFile(file) {
      this.file = file
    },
  },
}
</script>
