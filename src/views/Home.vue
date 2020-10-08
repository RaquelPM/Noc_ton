<template>
  <div class="w-100 h-100">
    <div v-bind:class="{escuro: modo=='true', claro: modo == 'false'}" class="d-flex justify-content-start align-items-center w-100 h-100 flex-column">
      <img class="mt-5" v-on:click="mudar_modo('true')" v-if="modo=='false'" src="@/assets/lua preta.svg"/>
      <img v-else src="@/assets/Vector.svg"/>
      <img class="mt-6" v-if="modo=='false'" src="@/assets/logo clara.svg"/>
    </div>
  </div>
</template>

<script>

export default {
  name: 'Home',
  data(){
    return{
      modo:'',
    }
  },
  methods:{
    mudar_modo: function(modo){
      localStorage.setItem('modo', modo);
      window.location.reload();
    }
  },
  created(){
    this.modo = localStorage.getItem('modo')
  }
}
</script>

<style>

.escuro{
  background:black;
  color:white;
}

.claro{
  background:white;
  color:black; 
}

.mt-6{
  margin-top: 25%;
}

</style>
