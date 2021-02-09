<template>
  <div class="d-flex justify-content-center align-items-center flex-column mx-3 m-blue">
    <p class="pergunta m-ye">O que já fizemos</p>
    <p class="titulo m-red ajuste_t_pur" >Portifólio</p>
    <div id="container_img">
      <img id="img_1" v-on:click="redirecionar(repos[0].html_url)" class=" clicavel troço_cinza m-blue_light"/>
      <img id="img_2" v-on:click="redirecionar(repos[1].html_url)" class="clicavel troço_cinza m-blue_light"/>
      <img id="img_3" v-on:click="redirecionar(repos[3].html_url)" class="clicavel troço_cinza m-blue_light"/>
    </div>
    <div>
    </div>
  </div>
</template>

<script>

import reposis from '@/services/reposi'

export default {
  name: 'HelloWorld',
  data(){
    return{
      repos:[],
    }
  },
  mounted(){
    reposis.listar().then(resp => {
      this.repos = resp.data;
      console.log(this.repos);
    }).catch(console.log('não foi possível'))
  },
  methods:{
    redirecionar: function(url){
      window.open(url, '_blank');
    }
  }
}
</script>

<style>
.troço_cinza{
  width: 270px;
  height: 200px;
  border:solid 2px #6C32B2;
}

.btn_mais{
  background: #6C32B2;
  border-radius: 4.3913px;
  border:none;
  width: 200px;
  height: 50px;
  
}

.borda_btn{
  background-color:rgba(108, 50, 178, 0.3);
  border-radius: 4.3913px;
}
</style>
