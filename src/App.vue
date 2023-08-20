<template>
    <PrincipalHeader> </PrincipalHeader>

    <section class="options">
      <p class="visualizar">Modo de Visualização:</p>
      <div class="buttons">
        <button class="btn-vertical" @click="changeView('vertical')"></button>
        <button class="btn-horizontal" @click="changeView('horizontal')"></button>
      </div>
    </section>

    <CardCar v-for="(car, index) in visibleCarInfo" :key="index"
    :imagem="car.veiculo_foto[0]" 
    :cidade="car.cidade_nome"
    :marca="car.veiculo_marca"
    :modelo="car.modelo_nome_pai" 
    :cambio="car.veiculo_cambio"
    :ano="car.ano_modelo"
    :valor="car.veiculo_valor"
    :km="car.veiculo_km"
    :verticalMode="viewMode"
    class="card-car"
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
    itemsPerPage: 5,       
    itemsToAdd: 5,         
    currentItems: 5,
    viewMode: 'horizontal',      
    };
  },
  methods: {
      changeView(mode){
        this.viewMode = mode;
      },
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

  @import url('https://fonts.googleapis.com/css2?family=Assistant:wght@300;400;500;700&display=swap');

  .options{
    margin-left: 5px;
  }
  .buttons{
    display: flex;
    gap: 5px;
    align-items: flex-end;
  }
  .btn-vertical{
    width: 25px;
    height: 40px;
  }
  .btn-horizontal{
    width: 40px;
    height: 25px;
  }
  .btn-vertical, .btn-horizontal{
    border: 1px solid black;
    border-radius: 5px;
    cursor: pointer;
  }
  .btn-vertical:hover, .btn-horizontal:hover{
    background-color: #fade00;
  }
  .visualizar{
    font-family: 'Assistant', sans-serif;
  }
  .final{
    height: 100px;
  }

</style>
