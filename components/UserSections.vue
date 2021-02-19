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
           <component v-if="currentSection" :is="currentSection"></component> 
        </keep-alive>
    </main>
</template>

<script>
import Respondents from './sections/Respondents.vue';
export default {
    name: 'UserSections',
    components: {
        Respondents,
    },

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
