<template>
  <div >
      <div class="respondents__list">
        <div class="respondents__condition-name">
            <h3 
            :style="{'color':respond.style.color}"
            >Условие {{index+1}}</h3>
            <select class="respondents__condition-select">
              <option 
                v-for="option in respond.options"
                :key="option.id"
                selected>{{option.title}}</option>
            </select>
        </div>
        <div class="respondents__condition-form">
          <div v-if="respond.isAge" class="respondents__age-form">
            <p>{{respond.name}}</p>
            <div class="respondents__diapozons">
              <label for="from">от</label>
              <input type="text" id="from"/>
              <label for="to">до</label>
              <input type="text" id="to"/>
            </div>
          </div>
          <div v-else-if="respond.isLoyaltyCartType" class="respondents__cart-type-form">
            <p>{{respond.name}}</p>
            <select class="respondents__cart-type-select">
              <option 
                v-for="cartType in respond.cartTypes"
                :key="cartType.id"
                selected
              >{{cartType.type}}</option>
            </select>
          </div>
          <div v-else-if="respond.isLoyaltyCartStatus" class="respondents__cart-status-form">
            <p>{{respond.name}}</p>
            <select class="respondents__cart-status-select">
              <option 
                v-for="cartStatus in respond.cartStatus"
                :key="cartStatus.id"
                selected
              >{{cartStatus.status}}</option>
            </select>
          </div>
          <div class="respondents__condition-buttons">
            <button class="respondents__add-button">
              <span>+ Добавить {{respond.name}}</span>
            </button>
            <button @click="removeCondition(index)"
                class="respondents__delete-button">
              <v-icon name="basket"/>
              <span>Удалить условие</span>
            </button>
          </div>
        </div>
      </div>
      </div>
</template>

<script>
export default {
    name: 'Conditions',
    props:{
        respond:{
            type: Object,
            required: true,
        },
        index:{
            type: Number,
            required: true
        }
    },
    methods:{
        removeCondition(index){
            this.$emit('delete',index);
        }
    }
}
</script>

<style>

</style>
