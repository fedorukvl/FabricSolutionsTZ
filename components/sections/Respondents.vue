<template>
  <div class="respondents">
      <h1 class="respondents__title">Добавить опрос</h1>
      <conditions 
        v-for="(respond,index) in responds"
        :key="respond.id"
        :style="{'backgroundColor':respond.style.backgroundColor}"
        class="respondents__condition"
        :respond="respond"
        :index="index"
        @delete="removeCondition"
        />
      <div class="respondents__add-condition">
          <div class="respondents__add-condition_info" @click="addRespond">
            <p class="respondents__add-condition_plus">+</p>
            <p class="respondents__add-condition_description">Нажмите, чтобы добавить условие выборки.</p>
            <p class="respondents__add-condition_description">Все условия связываются собой логическим "И"</p>    
          </div>
      </div>
      <div class="respondents__footer">
          <button class="respondents__footer_test-button">Протестировать опрос</button>
          <button class="respondents__footer_next-button">Далее</button>
      </div>
  </div>
</template>

<script>
import VIcon from '../VIcon.vue';
import Conditions from './Conditions.vue';
export default {
  components: { Conditions,VIcon },
  name:'Respondents',
  data(){
    return{
      responds:[],
      pickedConditionsCount:0,
    };
  },
  respondOptions:[
    {
        id: 1,
        name: 'Диапозон',
        isAge: true,
        style: {
          backgroundColor: '#fffcf5',
          color: '#a97a07'
        },
        options:[
          {
            id:1,
            title: 'Возраст респондента',
          }
        ]
      },
      {
        id: 2,
        name: 'Тип',
        isLoyaltyCartType: true,
        style: {
          backgroundColor: '#f8faff',
          color: '#214aa9'
        },
        cartTypes:[
          {
            id: 1,
            type: 'Gold',
          }
        ],
        options:[
          {
            id:1,
            title: 'Тип карты лояльности',
          }
        ]
      },
      {
        id: 3,
        name: 'Статус',
        isLoyaltyCartStatus: true,
        style: {
          backgroundColor: '#fafff8',
          color: '#30a525'
        },
        cartStatus:[
          {
            id: 1,
            status: 'Активна',
          }
        ],
        options:[
          {
            id:1,
            title: 'Статус карты лояльности',
          }
        ]
      },
  ],
  methods:{
    addRespond(){
      const optionsCount = this.pickedConditionsCount;
      const respondsList = this.responds;
      const optionsList = this.$options.respondOptions;
      if(optionsCount < optionsList.length){
        respondsList.push(optionsList[optionsCount]);
        this.pickedConditionsCount+=1;
      }else if(!respondsList.length){
        this.pickedConditionsCount=0;
      }
    },
    removeCondition(index){
      this.responds.splice(index,1);
    }
  }
}
</script>

<style lang="sass" src="@/media/sass/components/sections/Respondents.sass">

</style>
