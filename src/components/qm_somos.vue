<template>
    <div class="d-flex justify-content-center align-items-center flex-column mx-3">
        <p class="m-ye pergunta">Quem somos?</p>
        <div  class="d-flex justify-content-center align-items-center flex-column">
            <canvas id="flutuantes" class="mr-2"></canvas>
            <div id="qm_somos_text" class="position-absolute mx-4" >
                <p id="parte_d_cima" class="titulo">Equipe freelancer de</p>
                <p class="titulo m-red">desenvolvimento app/web.</p>
                <p class="m-blue texto">Nós da Noc.ton somos um time de desenvolvimento de plataformas digitais preocupados em entregar aos nossos clientes uma solução rápida, eficiente e de qualidade.</p>
            </div>
        </div>
    </div>
</template>

<script>
    export default{
        mounted(){
            const flutuantes = document.getElementById("flutuantes");
            flutuantes.width =  innerWidth-30;
            flutuantes.height =  375;
            const ctf = flutuantes.getContext("2d");

            function ren(x,y,w,h,style){
               
                this.draw = function(){
                    ctf.beginPath();
                    ctf.fillStyle = style;
                    ctf.fillRect(x,y, w,h);
                    ctf.fill();
                }

                this.update = function(estado, r){
                    if(r == 'r1'){
                        if(estado == 1){
                            if(y >= 15){
                                y = y-1;
                            }
                            console.log(y)
                        }
                        else{
                            if(y < 24){
                                y = y+1;
                            }
                        }
                    }
                    else{
                        if(estado == 1){
                            if(y >= 220){
                                y = y-1;
                            }
                            console.log(y)
                        }
                        else{
                            if(y < 230){
                                y = y+1;
                            }
                        }
                    }
                    this.draw();
                }
            }

            function cir(x,y,r,style){
                this.draw = function(){
                    ctf.beginPath();
                    ctf.fillStyle = style;
                    ctf.arc(x, y, r, 0, Math.PI * 2, true); 
                    ctf.fill();
                }

                this.update = function(estado, c){
                     if(c == 'c2'){
                        if(estado == 1){
                            if(y >= 30){
                                y = y-1;
                            }
                            console.log(y)
                        }
                        else{
                            if(y < 35){
                                y = y+1;
                            }
                        }
                    }
                    else{
                        if(estado == 1){
                            if(y >= 255){
                                y = y-1;
                            }
                            console.log(y)
                        }
                        else{
                            if(y < 265){
                                y = y+1;
                            }
                        }
                    }
                    this.draw();
                }
            }

            const object = document.getElementById("flutuantes")
            var rectObject = object.getBoundingClientRect().top;
            var compara = rectObject;

            function cb (){
                var rectObject = object.getBoundingClientRect().top;
                if(rectObject<compara){
                    compara = rectObject;
                    return 0;
                }
                else{
                    compara = rectObject;
                    return 1;
                }
            }

            var a = "";

            window.onscroll = () =>{
                    a = cb();
            }

            var r11 = new ren(15,0,190,103,'#F5C416');
            var r22 = new ren(innerWidth-125, 230, 110, 60, '#3DDC97')
            var cir11 = new cir(40,265,40,'#058ED9');
            var cir22 = new cir(innerWidth-52, 35, 19, '#FF0035');

            var r1 = new ren(15,0,128,70,'#F5C416');
            var r2 = new ren(innerWidth-125, 230, 110, 60, '#3DDC97');
            var cir1 = new cir(40,265,27,'#058ED9');
            var cir2 = new cir(innerWidth-52, 20, 19, '#FF0035');

            function animate(){
                requestAnimationFrame(animate);

                ctf.clearRect(0, 0, innerWidth, 400);
                if(innerWidth>=1000){
                    r11.update(a, 'r1');
                    r22.update(a, 'r2');
                    cir11.update(a,'c1');
                    cir22.update(a,'c2')
                }
                else{
                    r1.update(a, 'r1');
                    r2.update(a, 'r2');
                    cir1.update(a, 'c1');
                    cir2.update(a, 'c2');
                }
            }

            animate();
        }
    }
</script>

<style>
#parte_d_cima{
    line-height:20px !important;
}
</style>