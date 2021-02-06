<template>
  <div class="w-100 h-100">

    <div class="d-flex justify-content-center align-items-center w-100 h-100 flex-column">
      <canvas id="ani_lateral" ></canvas>
      <div class="position-absolute d-flex justify-content-center align-items-center w-100 h-100 flex-column">
        <img id="logo_branca" src="@/assets/logo_letraescura.svg"/>
        <img id="logo_escura" src="@/assets/logo escura.svg"/>
        <p class="frasesinha mt-5" >sua ideia em boas mãos</p>
      </div>
    </div>

    <div v-bind:class="{fechado:!aberto, aberto:aberto}" class="position-fixed flex-column fixed-bottom d-flex justify-content-end align-items-end mb-5">
      <div id="texto_no_claro" v-bind:class="{sumiu:!aberto, apareceu:aberto}" class="d-flex texto flex-column mr-3">
        <div class="d-flex">
          <img class="mb-1 mr-2" src="../assets/pontos/ponto_blue.svg"/>
          <a href="#qmsomos" class="link mb-1 azul" >Quem somos?</a>
        </div>
        <div>
          <img class="mb-1 mr-2" src="../assets/pontos/ponto_amarelo.svg"/>
          <a href="#oqfazemos" class="link mb-1 amarelo">O que fazemos?</a>
        </div>
        <div class="d-flex">
          <img class="mb-1 mr-2" src="../assets/pontos/ponto_vermelho.svg"/>
          <div class="d-flex flex-column" >
            <a href="#oqespeci" class="link vermelho">O que especificadamente</a>
            <p class="link vermelho mb-1">fazemos</p>
          </div>
        </div>
        <div>
          <img class="mb-1 mr-2" src="../assets/pontos/ponto_roxo.svg"/>
          <a href="#oqja" class="link mb-1 roxo" >O que ja fizemos.</a>
        </div>
        <div>
          <img class="mb-1 mr-2" src="../assets/pontos/ponto_colorido.svg"/>
          <a href="#equipe" class="link mb-1 texto" >Equipe Noc.ton</a>
        </div>
        <div>
          <img class="mb-1 mr-2" src="../assets/pontos/ponto_verde.svg"/>
          <a href="#contato" class="link verde" >Contato</a>
        </div>
      </div>
      <div @click="abrir" class="mr-3">
        <img id="head_b" class="clicavel" src="../assets/head_b.svg"/>
        <img id="head_d" class="clicavel" src="../assets/head_d.svg" />
      </div>
    </div>

    <div class="d-flex justify-content-start align-items-center flex-column">
      <div class="linha m-ye"></div>
      <qmsomos id="qmsomos"/>
      <div class="linha m-ye"></div>
      <oqfazemos id="oqfazemos"/>
      <oqespeci id="oqespeci"/>
      <div class="linha m-ye"></div>
      <oqja id="oqja"/>
      <div class="linha m-ye"></div>
      <equipe id="equipe"/>
      <div class="linha m-ye"></div>
      <contato id="contato"/>
    </div>
  </div>
</template>

<script>

import qmsomos from '../components/qm_somos.vue'
import oqfazemos from '../components/oq_fazemos.vue'
import oqespeci from '../components/oq_especi.vue'
import oqja from '../components/oq_ja.vue'
import equipe from '../components/equipe.vue'
import contato from '../components/contato.vue'

export default {
  name: 'Home',
  data(){
    return{
      aberto:false,
    }
  },
  components:{
    qmsomos,
    oqfazemos,
    oqespeci,
    oqja,
    equipe,
    contato,
  },
  methods:{
    abrir(){
      this.aberto=!this.aberto;
    }
  },
  mounted(){
    const ani_lateral = document.getElementById("ani_lateral");
    ani_lateral.width = innerWidth;
    ani_lateral.height = innerHeight;
  }
}
</script>


<style scope>

.ponto{
  font-size:100px;
  line-height:0px;
}

.link{
  text-decoration: none !important;
  font-size:15px !important;
}

a:hover {
    opacity:0.9;
}

.frasesinha{
  font-family: 'Comfortaa';
  font-style: bold;
  font-size: 16px;
  letter-spacing: 0.17em;
}

.linha{
    min-width: 141.96px;
    height: 0px;
    border-top: 2px solid #058ED9;
}

.fechado{
  -webkit-transition: height 0.7s;
  overflow: hidden;
  height: 90px;
}

.aberto{
  transition: height  0.5s;
  overflow: hidden;
  height : 250px;
}

.sumiu{
  -webkit-transition: opacity 0.7s;
  overflow: hidden;
  opacity: 0;
}

.apareceu{
  transition: opacity  0.9s;
  overflow: hidden;
  opacity : 1;
}

.amarelo{ 
  color:#FFD600;
}

.azul{
  color:#058ED9;
}

.vermelho{
  color: #FF0035;
}

.roxo{
  color:#6C32B2;
}

.verde{
  color:#3DDC97;
}
</style>

