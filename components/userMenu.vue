<template> 
  <header class="header">
      <div class="header__info">
          <form class="header__search-form">
              <input 
              type="text" 
              class="header__search-form_search"
              placeholder="Поиск по системе"
              >
              <button class="header__search-form_button">
                  <v-icon name='search'/>
              </button>
          </form>
          <div class="header__user-info">
              <div class="header__user-info_icon"></div>
              <div class="header__user-info_preview">
                <h3 class="header__user-info_name">Alexander C.</h3>
                <p class="header__user-info_grade">Администратор</p>
              </div>
          </div>
      </div>
      <div class="header__route-links">
        <nuxt-link v-if="formatedPath !==''" class="header__route-link" to="/">
          <v-icon name='home'/>
        </nuxt-link>
        <template v-if="formatedPath">
          <v-icon name='forward-arrow'/>
          <nuxt-link class="header__route-link" to="$route.path">
            {{formatedPath}}
          </nuxt-link>
        </template>
      </div>
  </header>
</template>

<script>
import VIcon from './VIcon.vue'
export default {
  name: 'UserMenu',
  components: { VIcon },
  computed:{
    formatedPath(){
      return this.$route.path.slice(1)==='interview'?'Опросы':this.$route.path.slice(1)==='users'?'Пользователи':this.$route.path.slice(1)==='blackList'?'Черный список':this.$route.path.slice(1)==='callCenter'?'Колл-центр':this.$route.path.slice(1)==='help'?'Помощь':'';
    }
  }
}
</script>

<style lang="sass" src="@/media/sass/components/UserMenu.sass">

</style>
