<template>
  <div>
    <!--Side Bar-->
    <Sidebar />
    <!--Page-->
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
    <!--Top Bar-->
    <Topbar />
    <!--Right Bar-->
    <Rightbar />
    <!--Footer-->
    <Footer />
  </div>
</template>

<script>
import Sidebar from '@/components/Sidebar'
import Topbar from '@/components/Topbar'
import Rightbar from '@/components/Rightbar'
import Footer from '@/components/Footer'
export default {
  name: 'Vertical',
  components: { Footer, Rightbar, Topbar, Sidebar },
}
</script>
