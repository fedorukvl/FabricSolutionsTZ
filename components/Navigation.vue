<template>
  <nav class="navigation">
        <ul class="navigation__list">
            <li class="navigation__link navigation__link_logo navigation__link_unhovered"></li>
            <ul class="navigation__section">
                <li>
                    <nuxt-link active-class="navigation__link_active" class="navigation__link" to="/respondents">
                        <v-icon name="respondent"/>
                        <p class="navigation__link_title">Опросы</p>
                    </nuxt-link>
                </li>
                <li>
                    <nuxt-link class="navigation__link" active-class="navigation__link_active" to="/users">
                        <v-icon name="users"/>
                        <p class="navigation__link_title">Пользователи</p>
                    </nuxt-link>
                </li>
                <li>
                    <nuxt-link class="navigation__link" active-class="navigation__link_active" to="/blackList">
                        <v-icon name="black-list"/>
                        <p class="navigation__link_title">Черные списки</p>
                    </nuxt-link>
                </li>
                <li>
                    <nuxt-link class="navigation__link" active-class="navigation__link_active" to="/callCenter">
                        <v-icon name="call-centr"/>
                        <p class="navigation__link_title">Колл-центр</p>
                    </nuxt-link>
                </li>
            </ul>
            <li>
                <nuxt-link class="navigation__link navigation__link_help navigation__link_unhovered" active-class="navigation__link_active" to="/help">
                    ?
                </nuxt-link>
            </li>
        </ul>
    </nav>
</template>

<script>
import VIcon from './VIcon'
export default {
    name: 'Navigation',
    components: {VIcon},
}
</script>

<style lang="sass" scoped src="@/media/sass/components/Navigation.sass"></style>
