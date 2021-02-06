<template>
    <div class="d-flex justify-content-center align-items-center flex-column mx-3">
        <p class="m-ye pergunta">O que fazemos?</p>
        <p class="titulo">Colocamos suas idéias em</p>
        <p class="titulo ajuste_t_ye m-red">Prática</p>
        <div id="container_ani_quad">
            <div id="div_ani_quad" class="d-flex justify-content-center align-items-center"><canvas id="ani_quad" class="m-blue_light"></canvas></div>
            <img id="escada_90g" src="../assets/ani_quad/escada_90g.svg" />
            <img id="escada_180g" src="../assets/ani_quad/escada_180g.svg" />
            <img id="l_90g" src="../assets/ani_quad/l_90g.svg" />
            <img id="l_180g" src="../assets/ani_quad/l_180g.svg" />
            <div id="text_ani" class="d-flex justify-content-center align-items-center">
                <p class="m-blue texto ml-4 mr-2">Uma ideia genial? Ninguém para executa-la? Nós estamos aqui. A Noc.ton está sempre pronta para consolidar os seus planos pelos preços mais justos.</p>
            </div>
        </div>
        <div class="d-flex">    
            <p class="titulo ajuste_t_cin">Sonhos</p>
            <p class="titulo ml-2">em</p>
            <p class="titulo m-red ajuste_t_ye ml-2">Realidade</p>
        </div>
        <p id="text_sonhos" class="texto m-blue ajuste mr-1">Com a nossa ajuda, os seus sonhos serão verdade. O seu futuro já começou. A festa, é sua. É nossa. É de quem quiser, quem vier.</p>
    </div>
</template>

<script>
export default{
    mounted(){
        const ani_quad = document.getElementById("ani_quad");
        ani_quad.width = 400;
        ani_quad.height = 250;

        const anq = ani_quad.getContext("2d");

        var escada_90g = document.getElementById("escada_90g");
        var escada_180g = document.getElementById("escada_180g");
        var l_90g = document.getElementById("l_90g");
        var l_180g = document.getElementById("l_180g");

        function objs(img,x,y){
            this.draw = function() {
                anq.drawImage(img,x,y);
            }
        }


        function l_180(x_l_90,x_escada_90,y_l_180, d_l_180, d_l_90, d_escada_90 ){
            this.draw_l_180 = function() {
                anq.drawImage(l_180g,170,y_l_180);
            }

            this.draw_l_90 = function() {
                anq.drawImage(l_90g,x_l_90,74);
            }

            this.draw_escada_90 = function() {
                anq.drawImage(escada_90g,x_escada_90,128);
            }

            this.update = function(){

                if(x_l_90<=70&&x_escada_90>=300&&y_l_180<=0){
                    d_l_180=1;
                }

                else if(x_l_90>=146&&x_escada_90<=200&&y_l_180>=74){
                    d_l_180=-1;
                }

                else if((d_l_90==1)||(d_l_90==-1)){
                    d_l_180=0;
                }

                y_l_180 = y_l_180+d_l_180;

                

                if(y_l_180>=74&&x_escada_90>=300&&x_l_90<=70){
                    d_l_90=1;
                }

                else if(y_l_180<=0&&x_escada_90<=200&&x_l_90>=146){
                    d_l_90=-1;
                }

                else if((d_escada_90==1)||(d_escada_90==-1)){
                    d_l_90=0;
                }

                x_l_90=x_l_90+d_l_90;


                if(y_l_180>=74&&x_l_90>=146&&x_escada_90>=300){
                    d_escada_90=1;
                }

                else if(y_l_180<=0&&x_l_90<=70&&x_escada_90<=200){
                    d_escada_90=-1;
                }

                else if((d_l_180==-1)||(d_l_180==1)){
                    d_escada_90=0;
                }

                x_escada_90=x_escada_90-d_escada_90;


                this.draw_l_180();
                this.draw_l_90();
                this.draw_escada_90();
            }
        }

        var statico = new objs(escada_180g, 170, 100);
        var l_18 = new l_180(70,300, 0, 1,0, 0);

        function animate(){
            requestAnimationFrame(animate);

            anq.clearRect(0, 0, innerWidth, 250);

            l_18.update();
            statico.draw();
        }

        animate();

    }
}

</script>

<style>
#escada_90g, #escada_180g, #l_180g, #l_90g{
    width:0px;
}

</style>