<template>
  <div class="layout">
    <navigation/>
    <div class="layout__main">
      <user-menu/>
      <user-sections/>
      <Nuxt />
    </div>
  </div>
</template>
<script>
import Navigation from '../components/Navigation.vue'
import UserMenu from '../components/userMenu.vue'
import UserSections from '../components/UserSections.vue'
export default {
  components:{
    Navigation,
    UserMenu,
    UserSections,
  }
}
</script>
<style lang="sass" scoped src="@/media/sass/core/layout.sass"></style>
