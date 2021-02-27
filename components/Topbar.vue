<template>
  <v-app-bar :clipped-left="clipped" color="#3bafda" fixed app>
    <!-- LOGO --><!---->
    <Logo :class="{ 'ml-4 mr-16': drawer, 'mr-2': drawer }" />
    <v-app-bar-nav-icon
      color="#fff"
      @click.stop="$store.commit('layout/CHANGE_DRAWER')"
    ></v-app-bar-nav-icon>
    <v-btn
      color="#fff"
      icon
      @click.stop="$store.commit('layout/CHANGE_POSITION_FOOTER')"
    >
      <v-icon>mdi-minus</v-icon>
    </v-btn>
    <v-spacer />
    <v-btn color="#fff" icon @click.stop="handleFullScreen">
      <v-icon>mdi-fullscreen</v-icon>
    </v-btn>
    <Notification />
    <Localization :option="'white'"></Localization>
    <Profile />
    <v-btn
      color="#fff"
      icon
      @click.stop="$store.commit('layout/CHANGE_RIGHT_DRAWER')"
    >
      <v-icon>mdi-cog</v-icon>
    </v-btn>
  </v-app-bar>
</template>

<script>
import Util from '@/util'
import Logo from './Logo'

export default {
  name: 'Topbar',
  components: { Logo },
  data() {
    return {
      clipped: true,
      fixed: false,
    }
  },
  computed: {
    drawer() {
      return this.$store.getters['layout/drawer']
    },
  },
  methods: {
    handleFullScreen() {
      Util.toggleFullScreen()
    },
  },
}
</script>
