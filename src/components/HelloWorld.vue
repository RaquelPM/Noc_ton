<template>
  <div class="w-100 h-100 background d-flex justify-content-center align-items-center flex-column">
    <div v-on:click="modo('light')" class="d-flex w-100 h-100 pr-5 justify-content-end align-items-center" >
      <img src="@/assets/Vector.svg"/>
    </div>
    <img src="@/assets/Group 30.svg" />
    <div v-on:click="modo('dark')"  class="d-flex w-100 h-100 justify-content-start align-items-center pl-5" >
      <img src="@/assets/Vector (1).svg"/>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  methods:{
    modo: function(modo){
      localStorage.setItem('modo', modo)
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
