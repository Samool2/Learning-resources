<template>
    <the-header title="Learning Resources"></the-header>
   <the-resources></the-resources>
</template>


<script>

import TheHeader from './components/layouts/TheHeader.vue';
import TheResources from './components/learning-resources/TheResources.vue';
    export default {
  components: {  TheHeader, TheResources },

    }
</script>


<style>
@import url('https://fonts.googleapis.com/css2?family=Karla:wght@600&family=Roboto+Flex:opsz@8..144&display=swap');
*{

    font-family:'Roboto Flex';
    list-style-type:none;
}





</style>