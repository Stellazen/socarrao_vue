
<template>
    <section class="container">
        <div class="imgCar" :style="{ backgroundImage: `url(${imagem})` }">
        <p class="cidade">{{ cidade }}</p>
        </div>
        <div class="infos_button">
            <section class="infos">
                <div class="infos_titulo">
                    <p class="marca">{{ marca }}</p>
                    <p class="modelo">{{ modelo }}</p>
                </div>
                <p class="infos_menores">{{ cambio }}</p>
                <p class="infos_menores">{{ ano }}</p>
                <p class="valor">R$ {{ valor.toLocaleString('pt-br', { style: 'currency', currency: 'BRL' }) }}</p>
                <p class="infos_menores">{{ km }} km</p>
            </section>
            <section class="buttons">
                <button class="buttonCard-1">Mais Informações</button>
                <button class="buttonCard-2">Falar no WhatsApp</button>
            </section>
        </div>
    </section>
</template>

<script>
export default {
    name: 'CardCar',

}
</script>

<script setup>
defineProps({
  imagem: String,
  cidade: String,
  marca: String,
  modelo: String,
  cambio: String,
  ano: Number,
  valor: String,
  km: Number
});
</script>

<style scoped>

    @import url('https://fonts.googleapis.com/css2?family=Assistant:wght@300;400;500;700&display=swap');
    
    .container{
        max-width: 500px;
        height: 180px;
        background-color: white;
        border-radius: 10px;
        margin: 10px;
        display: flex;
        align-items: center;
        gap: 10px;

    }
    .imgCar{
        width: 50%;
        height: 170px;
        background-size: cover;
        background-position: center;
        border-radius: 10px;
        margin-left: 5px;
    }
    .infos_button{
        max-width: 300px;
        align-items: center;
    }
    .infos_titulo{
        display: flex;
        gap: 10px;
        align-items: center;
    }
    .marca{
        font-size: 20px;
        font-weight: 500;
    }
    .modelo{
        color: #3174f1;
        font-weight: 500;
    }
    .valor{
        font-size: 18px;
        font-weight: 700;
    }
    .infos_menores{
        font-size: 13px;
    }
  
    .buttons{
        display: flex;
        flex-direction: column;
        gap:5px;
        align-items: center;
        justify-content: center;
    }
    .buttonCard-1, .buttonCard-2{
    width: 120px;
    height: 30px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-family: 'Assistant', sans-serif;
    }
    .buttonCard-1{
        border: 1px solid #3174f1;
        background-color: white;
    }
    .buttonCard-1:hover{
        background-color: #3174f1;
        color: white;
    }
    .buttonCard-2{
        background-color: #34af23;
    }
    .buttonCard-2:hover{
        background-color: white;
        border: 1px solid #34af23
    }
    p{
        font-family: 'Assistant', sans-serif;
    }
    .cidade{
        font-size: 12px;
        background-color: rgba(211, 211, 211, 0.781);
        width: 120px;
        border-radius: 5px;
        padding: 2px;
        margin: 2px;
    }
</style>