<template>
  <v-app dark>
    <CenterApp>
      <template #page>
        <h1 class="display-2 primary--text">Whoops {{ error.statusCode }}</h1>
        <p>Error {{ error.statusCode }}</p>
        <v-btn outlined color="primary" @click="$router.go(-1)">
          GET ME OUT OF HERE!
        </v-btn>
      </template></CenterApp
    >
  </v-app>
</template>

<script>
import CenterApp from '../components/widgets/CenterApp'
export default {
  components: { CenterApp },
  layout: 'empty',
  props: {
    error: {
      type: Object,
      default: null,
    },
  },
  data() {
    return {
      pageNotFound: 'Not Found',
      otherError: 'An error occurred',
    }
  },
  head() {
    const title =
      this.error.statusCode === 404 ? this.pageNotFound : this.otherError
    return {
      title,
    }
  },
}
</script>

<style scoped>
h1 {
  font-size: 20px;
}
</style>
