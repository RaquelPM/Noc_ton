<template>
  <div class="w-100 h-100 background d-flex justify-content-center align-items-center flex-column">
    <div class="w-100 h-100 justify-content-end d-flex">
      <div v-on:click="modo(false)" class="d-flex w-50 h-100 pr-5 justify-content-end align-items-center" >
        <img src="@/assets/Vector.svg"/>
      </div>
    </div>
    <img src="@/assets/Group 30.svg" />
    <div class="w-100 h-100 justify-content-start d-flex">
      <div v-on:click="modo(true)"  class="d-flex w-50 h-100 justify-content-start align-items-center pl-5" >
        <img src="@/assets/Vector (1).svg"/>
      </div>
    </div>
  </div>
</template>

<script>

import router from '@/router'

export default {
  methods:{
    modo: function(modo){
      localStorage.setItem('modo', modo)
      router.push({ name: 'Home'})
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.background {
  background: linear-gradient(to top right, #1E152A 50%, white 50%);
}

</style>
