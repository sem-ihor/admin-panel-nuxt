<template>
  <div>
    <!--Side Bar-->
    <Sidebar />
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
  name: 'Horizontal',
  components: { Footer, Rightbar, Topbar, Sidebar },
}
</script>
