<template>
  <v-row justify="center" align="center">
    <v-col cols="12" md="6" xs="12">
      <share-url-card />
    </v-col>
    <v-col cols="12" md="6" xs="12">
      <share-files-card />
    </v-col>
  </v-row>
</template>

<script>
import ShareUrlCard from '~/components/ShareUrlCard'
import ShareFilesCard from '~/components/ShareFilesCard'

export default {
  components: {
    ShareUrlCard,
    ShareFilesCard,
  },
}
</script>
