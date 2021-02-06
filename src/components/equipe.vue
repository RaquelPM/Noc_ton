<template>
    <div class="d-flex justify-content-center align-items-center flex-column mx-3 m-blue">
        <div class="d-flex justify-content-center align-items-center m-red">
            <p class="titulo_30 ml-3" >Equipe</p>
            <img id="logo_clara_pequena" class="ml-2 mb-4" src="../assets/logo_letraescura.svg"/>
            <img id="logo_escura_pequena" class="ml-2 mb-4" src="../assets/logo escura.svg"/>
        </div>
        <div id="container_inte" class="mr-4">
            <div id="inte_1" class="d-flex flex-column mx-3 mb-5 align-items-end">
                <div @click="pot_petrus" class="div_teste d-flex justify-content-end clicavel">
                    <canvas class="position-absolute" id="img_petrus"></canvas>
                    <img id="figura_petrus" class="position-absolute" src="../assets/escada_roxa_p.svg"/>
                    <div class="troço_cinza_redondo mr-3 mt-4"></div>
                </div>
                <div id="nameandp" class="d-flex flex-column align-items-center mr-4">
                    <p class="nome mt-3">Petrus</p>
                    <p class="funcao ajuste_t_pur">Mobile</p>
                </div>
            </div>

            <div id="inte_2" class="d-flex flex-column mx-3 mb-5 align-items-end">
                <div class="div_teste d-flex justify-content-center">
                    <canvas class="position-absolute" id="img_adson"></canvas>
                    <img id="figura_adson" class="position-absolute" src="../assets/ele_vermelho_a.svg"/>
                    <div class="troço_cinza_redondo ml-5 mt-4"></div>
                </div>
                <div id="nameandp" class="d-flex flex-column align-items-center mr-2">
                    <p class="nome mt-3">Adson</p>
                    <p class="funcao ajuste_t_red">Design</p>
                </div>
            </div>

            <div id="inte_3" class="d-flex flex-column mx-3 mb-5 align-items-end">
                <div class="div_teste d-flex justify-content-center ">
                    <canvas class="position-absolute" id="img_raquel"></canvas>
                    <img id="figura_raquel" class="position-absolute" src="../assets/escada_amarela_r.svg"/>
                    <div class="troço_cinza_redondo ml-5 mt-3"></div>
                </div>
                <div id="nameandr" class="d-flex flex-column align-items-center mr-2">
                    <p class="nome mt-3">Raquel</p>
                    <p class="funcao ajuste_t_ye">Frontend</p>
                </div>
            </div>

            <div id="inte_4" class="d-flex flex-column mx-3 mb-5 align-items-end clicavel">
                <div class="div_teste d-flex justify-content-center">
                    <canvas class="position-absolute" id="img_paulo"></canvas>
                    <img id="figura_paulo" src="../assets/ele_verde_pa.svg"/>
                    <div class="troço_cinza_redondo ml-5 mt-3"></div>
                </div>
                <div id="nameandr" class="d-flex flex-column align-items-center mr-2">
                    <p class="nome mt-3">Paulo</p>
                    <p class="funcao ajuste_t_agua">Backend</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default{
    mounted(){
        const canvas_paulo = document.getElementById("img_paulo");
        const canvas_raquel = document.getElementById("img_raquel");
        const canvas_adson = document.getElementById("img_adson");
        const canvas_petrus = document.getElementById("img_petrus");
        canvas_paulo.width =  95;
        canvas_paulo.height =  100;
        canvas_raquel.width =  95;
        canvas_raquel.height =  100;
        canvas_adson.width =  130;
        canvas_adson.height =  110;
        canvas_petrus.width =  85;
        canvas_petrus.height =  100;
        var figura_paulo = document.getElementById("figura_paulo");
        var figura_raquel = document.getElementById("figura_raquel");
        var figura_adson = document.getElementById("figura_adson");
        var figura_petrus = document.getElementById("figura_petrus");

        var cvp = canvas_paulo.getContext("2d");
        var cvr = canvas_raquel.getContext("2d");
        var cva = canvas_adson.getContext("2d");
        var cvpe = canvas_petrus.getContext("2d");
        

        function cvpp(img,x,y, dx, dy,cv, xf,yf){
            this.draw = function(){
                cv.drawImage(img, x, y);
            }

            this.update = function(){
                x=x+dx;
                y=y+dy;

                if(x>=xf){
                    if(innerWidth<=500){dx=-0.03;}
                    else{dx=-0.05}
                }
                else if(x<=5){
                    if(innerWidth<=500){dx=0.09;}
                    else{dx=0.15}
                }

                if(y>=yf){
                    if(innerWidth<=500){dy=-0.03;}
                    else{dy=-0.05}
                }

                else if(y<=5){
                    if(innerWidth<=500){dy=0.09;}
                    else{dy=0.15}
                }

                this.draw();
            }
        }

        var paulo = new cvpp(figura_paulo,5,5,0.1,0.1,cvp,10,10);
        var raquel = new cvpp(figura_raquel,5,5,0.1,0.1,cvr,15,15);
        var adson = new cvpp(figura_adson,5,5,0.1,0.1,cva,8,8);
        var petrus = new cvpp(figura_petrus,5,5,0.1,0.1,cvpe,12,12);

        function animate(){
        requestAnimationFrame(animate);

        cvp.clearRect(0, 0, 95, 100);
        paulo.update();
        
        cvr.clearRect(0, 0, 95, 100);
        raquel.update();

        cva.clearRect(0, 0, 120, 110);
        adson.update();

        cvpe.clearRect(0, 0, 85, 100);
        petrus.update();

      }

      animate();

    },
    methods:{
        pot_petrus(){
            window.location.href='https://petrus.codes';
        }
    }
}
</script>

<style>
    #figura_paulo,#figura_raquel,#figura_adson,#figura_petrus{
        width:0px;
    }
    .titulo_30{
        font-family: 'Comfortaa';
        font-size: 30px;
    }

    .troço_cinza_redondo{
        width: 90px;
        height: 90px;
        border-radius:50px;
        background: #C4C4C4;
    }

    .div_teste{
        width:140px;
        height:115px;
    }

    .nome{
        font-family:"Comfortaa";
        font-size: 18px;
        line-height: 10px;
    }

    .funcao{
        font-family:"Comfortaa";
        font-size: 18px;
        line-height: 10px;
    }
</style>