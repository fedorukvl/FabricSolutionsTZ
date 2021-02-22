<template>
  <div >
      <div class="respondents__list">
        <div class="respondents__condition-name">
            <h3 
            :style="{'color':respond.style.color}"
            >Условие {{respond.id}}</h3>
            <select class="respondents__condition-select">
              <option 
                v-for="option in respond.options"
                :key="option.id"
                selected>{{option.title}}</option>
            </select>
        </div>
        <div class="respondents__condition-form">
          <div 
            v-for="(diapazon,index) in respond.diapazons"
            :key="index" 
            class="respondents__age-form">
                <p>{{respond.name + diapazon.id}}</p>
                <div class="respondents__diapozons">
                <label for="from">от</label>
                <input type="text" id="from" :value="diapazon.from"/>
                <label for="to">до</label>
                <input type="text" id="to" :value="diapazon.to"/>
                </div>
          </div>
          <div 
            v-for="(cartType,index) in respond.cartTypes"
            :key="index" 
            class="respondents__cart-type-form">
                <p>{{respond.name + cartType.id}}</p>
                <select class="respondents__cart-type-select">
                <option selected>{{cartType.type}}</option>
                </select>
          </div>
          <div 
            v-for="(cartStatus,index) in respond.cartStatus"
            :key="index" 
            class="respondents__cart-status-form">
                <p>{{respond.name + cartStatus.id}}</p>
                <select class="respondents__cart-status-select">
                <option selected>{{cartStatus.status}}</option>
                </select>
          </div>
          <div class="respondents__condition-buttons">
            <button 
                class="respondents__add-button"
                @click="addCondition(index,respond.type)"
            >
              <span>+ Добавить {{respond.name}}</span>
            </button>
            <button @click="removeCondition(index,respond.type)"
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
        removeCondition(index,type){
            this.$emit('delete',index,type);
        },
        addCondition(index,type){
            this.$emit('add',index,type)
        },
    },
}
</script>
