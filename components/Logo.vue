<template>
  <nuxt-link to="/">
    <span v-if="drawer" class="logo-container">
      <v-img :src="require('@/static/Logo.svg')" />
      <!--      <img class="logo-img" src="@/static/Logo.svg"-->
    </span>
    <span v-else class="logo-container">
      <v-img :src="require('@/static/Logo-mini.svg')" /></span
  ></nuxt-link>
</template>
<script>
export default {
  computed: {
    drawer() {
      return this.$store.getters['layout/drawer']
    },
  },
}
</script>
