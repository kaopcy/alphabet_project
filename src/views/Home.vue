<template>
  <div class="home">
    <Footer :title="10" color="white"/>
  </div>
</template>

<script>
// @ is an alias to /src
  import Footer from '@/components/layout/Footer.vue'
export default {
  name: 'Home',
  components: {
    Footer
  }
}
</script>
<style>
img{
  height: auto;
  width: 1510px;
}
</style>
