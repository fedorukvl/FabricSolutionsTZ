<template>
  <div class="respondents">
      <h1 class="respondents__title">Добавить опрос</h1>
      <!-- <div 
        v-for="respond in responds"
        :key="respond.id"
        class="respondents__list"
        >
      </div>
       -->
      <div class="respondents__add-condition">
          <div class="respondents__add-condition_info">
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
export default {

}
</script>

<style lang="sass" scoped src="@/media/sass/components/sections/Respondents.sass">

</style>
