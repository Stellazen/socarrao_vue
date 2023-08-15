<template>
  <header>
  <PrincipalHeader />
  </header>
  <body>
    <CardCar v-for="(car, index) in carInfo.slice(0,5)" :key="index"
    :imagem="car.veiculo_foto[0]" 
    :cidade="car.cidade_nome"
    :marca="car.veiculo_marca"
    :modelo="car.veiculo_modelo" 
    :cambio="car.veiculo_cambio"
    :ano="car.ano_modelo"
    :valor="car.veiculo_valor"
    :km="car.veiculo_km"
    />
  </body>
</template>

<script>
// import { RouterLink, RouterView } from 'vue-router'
import CardCar from './components/CardCar.vue';
import PrincipalHeader from './components/PrincipalHeader.vue';
import carInfo from '../data.json';

export default {
  name: 'App',
  components: {
    PrincipalHeader,
    CardCar
  },
  data(){
    return{
      carInfo : carInfo
    }
  }
}
</script>

<style scoped>

</style>
