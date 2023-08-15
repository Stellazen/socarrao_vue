
<template>
    <section class="container">
        <div class="imgCar" :style="{ backgroundImage: `url(${imagem})` }"></div>
        <div class="infos_button">
            <section class="infos">
                <p> {{ cidade }}</p>
                <p>{{ marca }}</p>
                <p>{{ modelo }}</p>
                <p>{{ cambio }}</p>
                <p>{{ ano }}</p>
                <p>{{ valor }}</p>
                <p>{{ km }}</p>
            </section>
            <section class="buttons">
                <button class="buttonCard-1">Mais Informações</button>
                <button class="buttonCard-2">Falar no WahtsApp</button>
            </section>
        </div>
    </section>
</template>

<script setup>

defineProps({
  imagem: String,
  cidade: String,
  marca: String,
  modelo: String,
  cambio: String,
  ano: String,
  valor: String,
  km: String
});
</script>

<style scoped>
    .container{
        height: 200px;
        background-color: white;
        border-radius: 10px;
        margin: 10px;
        display: flex;
        align-items: center;
        padding: 5px;
    }
    .imgCar{
        width: 40%;
        height: 180px;
        background-size: cover;
        background-position: center;
        border-radius: 10px;
        margin: 0 10px 0 10px;
    }
    .buttons{
        display: flex;
        flex-direction: column;
        gap:5px;
        align-items: center;
    }
    .buttonCard-1, .buttonCard-2{
    width: 200px;
    height: 30px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    }
    .buttonCard-1{
        border: 2px solid #fade00;
        background-color: white;
    }
    .buttonCard-2{
        background-color: #34af23;
    }
</style>