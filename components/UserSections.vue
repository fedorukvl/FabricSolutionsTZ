<template>
    <main>
        <ul class="user-sections">
            <li 
                v-for="section in sections"
                :key="section.id"
                class="user-sections__section"
            >
                <button 
                @click="changeSection(section.name)"
                class="user-sections__button"
                :class="{'user-sections__button_active': (section.name===currentSection)
                }">{{section.title}}</button>
            </li>
        </ul>
        <keep-alive>
           <!-- <component :is=""> при выборе раздела будет рендерится необходимый компонент </component> -->
        </keep-alive>
    </main>
</template>

<script>
export default {
    name: 'UserSections',

    data(){
        return{
        currentSection: '',
        sections:[
            {id: 1,title: 'Параметры',name:'Params'},
            {id: 2,title: 'Вопросы',name:'Questions'},
            {id: 3,title: 'Логика',name:'Logic'},
            {id: 4,title: 'Условия',name:'Conditions'},
            {id: 5,title: 'Респонденты',name:'Respondents'}]
        }
    },

    methods:{
        changeSection(section){
            this.currentSection = section;
        },
    }
}
</script>

<style scoped lang="sass" src="@/media/sass/components/UserSections.sass">

</style>
