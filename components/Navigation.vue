<template>
  <div class="navigation">
        <ul class="navigation__list">
            <li class="navigation__link navigation__link_logo"></li>
            <li class="navigation__link">
                <v-icon name="respondent"/>
                <p class="navigation__link_title">Опросы</p>
            </li>
            <li class="navigation__link">
                <v-icon name="users"/>
                <p class="navigation__link_title">Пользователи</p>
            </li>
            <li class="navigation__link">
                <v-icon name="black-list"/>
                <p class="navigation__link_title">Черные списки</p>
            </li>
            <li class="navigation__link">
                <v-icon name="call-centr"/>
                <p class="navigation__link_title">Колл-центр</p>
            </li>
        </ul>
    </div>
</template>

<script>
import VIcon from './VIcon'
export default {
    name: 'Navigation',
    components: {VIcon},
}
</script>

<style>

</style>
