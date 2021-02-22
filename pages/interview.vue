<template>
  <div class="users-info"> 
    <user-sections/>
  </div>
</template>

<script>
import UserSections from '../components/UserSections.vue'
export default {
  name: 'respondents',
  components: {
    UserSections,
  },
};
</script>
