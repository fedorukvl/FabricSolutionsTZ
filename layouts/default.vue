<template>
  <div class="layout">
    <navigation/>
    <div class="layout__main">
      <Nuxt />
    </div>
  </div>
</template>
<script>
import Navigation from '../components/Navigation.vue'
export default {
  components:{
    Navigation,
  }
}
</script>
<style></style>
