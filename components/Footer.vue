<template>
  <v-footer :absolute="!fixed" style="z-index: 100" app>
    <span>&copy; Tangram {{ new Date().getFullYear() }}</span>
  </v-footer>
</template>

<script>
export default {
  name: 'Footer',
  // eslint-disable-next-line vue/require-prop-types
  computed: {
    fixed() {
      return this.$store.getters['layout/fixed']
    },
  },
}
</script>
