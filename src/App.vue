<script setup>
import { reactive, watch } from 'vue';

import Cabecalho from './components/Cabecalho.vue';
import Formulario from './components/Formulario.vue';

const estado = reactive({
    filtro: '',
    numero1: '',
    numero2: '',
    resultado: '',
})

const getSomar = () => {

    const { numero1, numero2 } = estado;
    estado.resultado = numero1 + numero2;

}

const getSubtrair = () => {
    
    const { numero1, numero2 } = estado;
    estado.resultado = numero1 - numero2;
}

const getMultiplicar = () => {
    
    const { numero1, numero2 } = estado;
    estado.resultado = numero1 * numero2;
}

const getDivisao = () => {
    
    const { numero1, numero2 } = estado;
    estado.resultado = numero1 / numero2;
}

const getOperacao = () => {
    const { filtro } = estado;
    console.log('Chamando getOperacao...')

    switch (filtro) {
      case 'adicao': 
        return getSomar();
      case 'subtracao': 
        return getSubtrair();
      case 'multiplicacao': 
        return getMultiplicar();
      case 'divisao': 
        return getDivisao();
    }
  }

  watch([() => estado.numero1, () => estado.numero2], () => {
    getOperacao();
});



</script>

<template>
  <div class="container">
    <Cabecalho />
    <Formulario :resultado="estado.resultado" :filtro="evento => estado.filtro = evento.target.value" :numero1="evento => estado.numero1 = parseInt(evento.target.value)" :numero2="evento => estado.numero2 = parseInt(evento.target.value)" />
    
  </div>
</template>

<style scoped>

  .form-control {
    border: 1px solid #000;
  }

  .text-white {
    font-size: 24px;
  }

</style>
