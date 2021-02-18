<template>
    <main>
        <ul class="user-sections">
            <li class="user-sections__section">
                <button class="user-sections__button">Параметры</button>
            </li>
            <li class="user-sections__section">
                <button class="user-sections__button">Вопросы</button>
            </li>
            <li class="user-sections__section">
                <button class="user-sections__button">Логика</button>
            </li>
            <li class="user-sections__section">
                <button class="user-sections__button">Условия</button>
            </li>
            <li class="user-sections__section">
                <button class="user-sections__button
                user-sections__button_active">Респонденты</button>
            </li>
        </ul>
        <keep-alive>
           <!-- <component :is=""> при выборе раздела будет рендерится необходимый компонент </component> -->
        </keep-alive>
    </main>
</template>

<script>
export default {

}
</script>

<style scoped lang="sass" src="@/media/sass/components/UserSections.sass">

</style>
