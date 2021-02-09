<template>
  <div id="app" class="d-flex justify-content-center align-items-center">
    <home/>
  </div>
</template>

<script>

import home from './views/Home.vue'

export default{
  components:{
    home,
  }
}
</script>

<style>
#app {
  height: 100vh;
  width: 100vw;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-leave-to{
  transition: opacity .1s;
}
.fade-enter, .fade-leave /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
