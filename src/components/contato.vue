<template>
    <div class="d-flex justify-content-center align-items-center flex-column mx-3 w-100">
        <p class="pergunta m-red ajuste_t_agua">Precisa de nós?</p>
        <div class="w-100 cinza d-flex justify-content-center align-items-center flex-column pb-5">
            <p class="texto m-red entre mt-5">Entre em contato</p>
            <img id="envelopinho" @click="copy" class="clicavel" src="../assets/envelope-b.svg"/>
            <img @click="copy" class="clicavel" src="../assets/envelope-p.svg" />
            <textarea id="f" ref="copiar" class="mb-1">contato@nocton.tech</textarea>
            <div @click="copy" class="email titulo m-blue d-flex">
                <p class="mt-3 ml-4">contato</p>
                <p class="mt-3 ajuste_t_blue">@</p>
                <p class="mt-3">nocton</p>
                <p class="mt-3 mr-3 ajuste_t_blue">.tech</p>
            </div>
            <p class="frasesinha entre m-ye" >Sua ideia em boas mãos.</p>
            <img id="logo_estreita_clara" src="../assets/logo_estreita_clara.svg" class="pb-4" />
            <img id="logo_estreita_escura" src="../assets/logo_estreita_escura.svg" class="pb-4" />
            <div class="div_onda d-flex flex-column">
                <canvas id="c"></canvas>
                <div class="div_back w-100"></div>
            </div>
        </div>
    </div>
</template>

<script>

export default{
    methods:{
        copy(){
            var copyTextarea = this.$refs.copiar;
        
            copyTextarea.select();

            try {
            var successful = document.execCommand('copy');
            successful ? 'sim!' : 'não!';
            alert('Copiado, aguardamos ansiosamente pelo seu contato :)');
            } catch (err) {
            alert('Opa, Não conseguimos copiar o texto, é possivel que o seu navegador não tenha suporte, tente usar Crtl+C.');
            }
        }
    },
    mounted(){
        const canvas = document.getElementById("c");
        canvas.width =  innerWidth
        if(innerWidth<=500){canvas.height =  65}
        else if(innerWidth<=950){canvas.height = 68}
        else{canvas.height =  95}
        const ctx = canvas.getContext("2d");  

        let increment = 0.01;

        function animate(){

            requestAnimationFrame(animate);

            ctx.clearRect(0,0, innerWidth, innerHeight)
            ctx.beginPath();

            ctx.moveTo(0,100/2);

            for(let i = 0; i<innerWidth; i++){
                ctx.lineTo(i, 70 + Math.sin(i * 0.003 + increment) * 50)
                ctx.lineTo(0, 100)
                ctx.lineTo(innerWidth, 100)
            }
            ctx.stroke();
            ctx.strokeStyle = '#058ED9'
            increment += 0.04;
        }

        animate();
    },
}

</script>

<style>

#f{
    width:0px;
    height:0px;
    outline:none;
    opacity:0;
}

.cinza{
    background: #1E152A;
}

.email{
    font-size:18px !important;
    letter-spacing: 0.17em;
    line-height:8px;
    background: #eaeaea;
}

.entre{
    color:white;
}

.div_onda{
    width:100%;
    height:190px
}

.div_back{
    min-height:180px;
    background: #058ED9;
    border:none;
}

</style>