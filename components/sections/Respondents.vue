<template>
  <div class="respondents">
      <h1 class="respondents__title">Добавить опрос</h1>
      <div 
        v-for="(respond, index) in responds"
        :key="respond.id"
        class="respondents__list"
        >
        <div class="respondents__condition-name">
            <h3>Условие {{index+1}}</h3>
            <select>
              <option 
                v-for="option in respond.options"
                :key="option.id"
                selected>{{option.title}}</option>
            </select>
        </div>
        <div class="respondents__condition-form">
          <div v-if="respond.isAge" class="respondents__age-form">
            <p>{{respond.name}}</p>
            <label for="from">от</label>
            <input type="text" id="from"/>
            <label for="to">до</label>
            <input type="text" id="to"/>
          </div>
          <div v-else-if="respond.isLoyaltyCartType" class="respondents__cart-type-form">
            <p>{{respond.name}}</p>
            <select>
              <option 
                v-for="cartType in respond.cartTypes"
                :key="cartType.id"
                selected
              >{{cartType.type}}</option>
            </select>
          </div>
          <div v-else-if="respond.isLoyaltyCartStatus" class="respondents__cart-status-form">
            <p>{{respond.name}}</p>
            <select>
              <option 
                v-for="cartStatus in respond.cartStatus"
                :key="cartStatus.id"
                selected
              >{{cartStatus.status}}</option>
            </select>
          </div>
          <div class="respondints__condition-buttons">
            <button>
              <span>+ Добавить {{respond.name}}</span>
            </button>
            <button>
              <span>Удалить условие</span>
              <v-icon name="basket"/>
            </button>
          </div>
        </div>
      </div>
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
export default {
  name:'Respondents',
  component: {VIcon},
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
      }
    }
  }
}
</script>

<style lang="sass" scoped src="@/media/sass/components/sections/Respondents.sass">

</style>
