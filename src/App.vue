<template>
  <v-app class="main">
    <v-main>
       <v-container>
           <!-- <VVFormValidate /> -->
           <!-- <FormValidations />
           <VueFormValidations /> -->
           <router-view></router-view>
       </v-container>
    </v-main>
  </v-app>
</template>

<script>
// import FormValidations from './components/FormValidations.vue';
// import VueFormValidations from './components/VueFormValidations.vue';
// import VVFormValidate from './components/VVFormValidate.vue';

export default {
  name: 'App',

  components: {
    // FormValidations,
    // VueFormValidations,
    // VVFormValidate
},

  data: () => ({
    //
  }),
};
</script>

<style scoped>
  .main{
      background-color:white;
   }



</style>
