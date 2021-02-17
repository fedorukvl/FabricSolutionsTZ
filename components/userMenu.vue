<template> 
  <header class="header">
      <div class="header__info">
          <form class="header__search-form">
              <input 
              type="text" 
              class="header__search-form_search"
              placeholder="Поиск по системе"
              >
              <button class="header__search-from_button">
                  <v-icon name='search'/>
              </button>
          </form>
          <div class="header__user-info">
              <div class="header__user-info-icon"></div>
              <h3 class="header__user-info_name">Alexander C.</h3>
              <p class="header__user-info_grade">Администратор</p>
          </div>
      </div>
      <div class="header__route-links">
        <v-icon name='home'/>
        <v-icon name='forward-arrow'/>
        <!-- имя роута -->
      </div>
  </header>
</template>

<script>
import VIcon from './VIcon.vue'
export default {
  components: { VIcon },
    name: 'UserMenu',
}
</script>

<style>

</style>
