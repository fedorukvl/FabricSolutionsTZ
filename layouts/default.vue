<template>
  <div class="layout">
    <navigation/>
    <div class="layout__main">
      <user-menu/>
      <nuxt />
    </div>
  </div>
</template>
<script>
import Navigation from '../components/Navigation.vue'
import UserMenu from '../components/userMenu.vue'
export default {
  components:{
    Navigation,
    UserMenu
  }
}
</script>
<style lang="sass" scoped src="@/media/sass/core/layout.sass"></style>
