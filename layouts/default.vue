<template>
  <v-app v-resize="onResize" dark>
    <vertical
      v-if="layout.layoutType === 'vertical'"
      :layout="layout.layoutType"
    />
  </v-app>
</template>

<script>
import { mapState } from 'vuex'
import Vertical from './vertical'
export default {
  components: { Vertical },
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/',
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire',
        },
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js',
      windowSize: {
        x: 0,
        y: 0,
      },
    }
  },
  mounted() {
    this.onResize()
  },

  methods: {
    onResize() {
      this.windowSize = { x: window.innerWidth, y: window.innerHeight }
      this.$store.commit('layout/CHANGE_SIZE_WINDOW', this.windowSize)
    },
  },
  computed: mapState(['layout']),
}
</script>
