<template>
	
  <Navi/>
  <router-view />

</template>

<script>
import Navi from './components/Navi.vue';
export default {
components: { Navi },
name: "App",
components: {
  Navi,  
}

};

</script>

<style lang="scss">
* {
    text-decoration: none;
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'poppins';                                     
  }

  body {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
}

  html {
    height: 100%;
    scroll-behavior: smooth;
  }

</style>
