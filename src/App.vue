<template>
    <PrincipalHeader />

    <CardCar v-for="(car, index) in visibleCarInfo" :key="index"
    :imagem="car.veiculo_foto[0]" 
    :cidade="car.cidade_nome"
    :marca="car.veiculo_marca"
    :modelo="car.modelo_nome_pai" 
    :cambio="car.veiculo_cambio"
    :ano="car.ano_modelo"
    :valor="car.veiculo_valor"
    :km="car.veiculo_km"
    />
  
  <div id="final" class="final"></div>
</template>

<script>
import CardCar from './components/CardCar.vue';
import PrincipalHeader from './components/PrincipalHeader.vue';
import carInfo from '../data.json';

export default {
  name: 'App',
  components: {
    PrincipalHeader,
    CardCar,
  },
  data(){
    return {
    carInfo: carInfo,
    itemsPerPage: 5,       // Quantidade inicial de itens exibidos
    itemsToAdd: 5,         // Quantidade de itens a serem adicionados
    currentItems: 5,       // Quantidade atual de itens exibidos
    };
  },
  computed: {
  visibleCarInfo() {
    return this.carInfo.slice(0, this.currentItems);
    },
  },
  mounted() {
    const options = {
      root: null,
      threshold: 0.5,
    };

    const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        this.currentItems += this.itemsToAdd;
        console.log('Elemento visível');
      } else {
        console.log('Elemento não visível');
      }
    });
  }, options);

    const elementToObserve = document.querySelector('#final');
    observer.observe(elementToObserve);
  },
};
</script>

<style scoped>
  .final{
    height: 100px;
  }
</style>
