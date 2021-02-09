<template>
    <div class="d-flex justify-content-center align-items-center flex-column mx-3 m-blue_plus_ye">
        <p class="m-ye pergunta ajuste" >O que especificadamente fazemos?</p>
      <p id="appsesites" class="m-red w-100 titulo ajuste_t_red">Apps e sites</p>
      <div id="ex">
        <div id="ex_sites" class="mx-3 d-flex justify-content-center align-items-center flex-column">
          <img id="retangulo_cubo_claro" src="@/assets/retangulo_cubo.svg"/>
          <img id="retangulo_cubo_preto" src="@/assets/retangulo_cubo_preto.svg"/>
          <p class="texto ajuste m-blue">Sua ideia de maneira portátil, no bolso de cada cliente, em qualquer momento e lugar. Com a nossa eficiência.</p>
        </div>
        <div id="ex_apps" class="mx-3 d-flex justify-content-center align-items-center flex-column">
          <div id="retangulo_red" class="d-flex align-content-center justify-content-center">
            <canvas id="c_mouse" ></canvas>
          </div>
          <p class="texto ajuste m-blue">Atraia internautas! Sua ideia no mundo web, em forma de site. Com a qualidade noc.ton.</p>
          <img id="mouse_branco" src="../assets/mouse_branco.svg"/>
          <img id="mouse_preto" src="../assets/mouse.svg"/>
          <img id="maozin" src="../assets/maozin.webp"/>
          <img id="maozina" src="../assets/maozin.png"/>
        </div>
      </div>
    </div>
</template>

<script>
  export default{
    mounted(){
      const canvas_mouse = document.getElementById("c_mouse");
      canvas_mouse.width =  95;
      canvas_mouse.height =  100;
      var img = document.getElementById("mouse_branco");
      var img1 = document.getElementById("mouse_preto");
      var maozin = document.getElementById("maozin");
      var maozina = document.getElementById("maozina");
      var content = document.getElementById("retangulo_cubo_preto").width;
      const ctm = canvas_mouse.getContext("2d");

     function m(x,dx,y,dy,imge, w, h, sub){
        this.x=x;
        this.dx=dx;
        this.y=y;
        this.dy=dy;
        this.img=imge;
        this.sub = sub;

        this.draw = function(){
          ctm.drawImage(img,x,y,w,h);
        }

        this.update = function(){
           
          if(x<40&&y<39){
            dx=-dx;
            dy=-dy;
          }

          if(y>75&&x>75){
            dy=-dy;
            dx=-dx;
          }

          if(x<45){
            img=sub;
            
            x=x+0.01
            y=y+0.01
          }

          if(x>40.5){
            w=15;
            h=20;
            img = imge;
            x-=dx;
            y-=dy;
          }

          y -= dy;
          x -=dx;

          this.draw();
        }
      }

      var mouse = new m(75,0.2,75,0.2, img, 15, 20, maozin);
      var mouse1 = new m(75,0.2,75,0.2,img1,15,20, maozina);

      function animate(){
        requestAnimationFrame(animate);

        ctm.clearRect(0, 0, 95, 100);

        if(content>0){
          mouse1.update();
        }
        else{
          mouse.update();
        }

      }

      animate();
    }
  }
</script>

<style>

#retangulo_red{
    height: 100px;
    width: 119px;
    border-radius:10px;
    border-top: 25px solid #FF0035;
    border-bottom: 12px solid #FF0035;
    border-left: 12px solid #FF0035;
    border-right: 12px solid #FF0035;
    margin-bottom:48px;
    max-width:150px;
}

#maozin, #maozina, #mouse_branco, #mouse_preto{
  width:0px;
}

</style>