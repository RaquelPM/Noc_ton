<template>
  <div class="d-flex justify-content-center align-items-center flex-column mx-3 m-blue">
    <p class="pergunta m-ye">O que já fizemos</p>
    <p class="titulo m-red ajuste_t_pur" >Portifólio</p>
    <div id="container_img">
      <div id="img_1" class="troço_cinza m-blue_light"></div>
      <div id="img_2" class="troço_cinza m-blue_light"></div>
      <div id="img_3" class="troço_cinza m-blue_light"></div>
    </div>
    <div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
}
</script>

<style>
.troço_cinza{
  width: 272px;
  height: 208px;
  border:solid 2px #6C32B2;
  background: #C4C4C4;
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
