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
        @add="addCondition"
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
let lastDiapazonId = 1;
let lastCartStatusId = 1;
let lastCartTypeId = 1;
import VIcon from '../../VIcon.vue';
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
        type: 'diapazons',
        style: {
          backgroundColor: '#fffcf5',
          color: '#a97a07'
        },
        options:[
          {
            id:1,
            title: 'Возраст респондента',
          }
        ],
        diapazons:[
          {
            id: 1,
            from: null,
            to: null,
          }
        ]
      },
      {
        id: 2,
        name: 'Тип',
        type:'cartTypes',
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
        type: 'cartStatus',
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
    removeCondition(index,type){
      lastDiapazonId = 1;
      lastCartStatusId = 1;
      lastCartTypeId = 1;
      this.responds[index][type].splice(1);
      this.responds.splice(index,1);
    },
    generateId(value){ // Добавил генерацию ID для диапазона/статуса/типа карты
      switch(value){
        case 'diapazons':
          return lastDiapazonId++;
          break;
        case 'cartTypes':
          return lastCartTypeId++;
          break;
        case 'cartStatus':
          return lastCartStatusId++;
          break;
        default:
          return false;
      }
    },
    addCondition(index,type){
      this.generateId(type)
      switch(type){
        case 'diapazons':
          this.responds[index][type].push({
            id: lastDiapazonId ,
            from: null,
            to: null,
          });
          break;
        case 'cartTypes': 
          this.responds[index][type].push({
            id: lastCartTypeId,
            type: 'Gold',
          });
          break;
        case 'cartStatus':
          this.responds[index][type].push({
            id: lastCartStatusId,
            status: 'Активна',
          });
          break;
        default:
          return false;
      };
    }
  }
}
</script>

<style lang="sass" src="@/media/sass/components/sections/Respondents.sass">

</style>
