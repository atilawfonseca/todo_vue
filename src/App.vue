<script setup>

import {reactive} from 'vue';
import Cabecalho from './components/Cabecalho.vue';
import Formulario from './components/Formulario.vue';
import ListaDeTarefas from './components/ListaDeTarefas.vue';

const estado = reactive({
  filtro:'',
  tarefaTemp: '',
  tarefas: [
  {
    titulo: "Estudar ES6",
    finalizada: false
  },
  {
    titulo: "Estudar JavaScript",
    finalizada: false
  },
  {
    titulo: "Estudar Matlab",
    finalizada: true
  },
  ]
}
);
const getAtividadePendente = () => {
  return estado.tarefas.filter(tarefa => !tarefa.finalizada);
}

const getAtividadeFinalizada = () => {
  return estado.tarefas.filter(tarefa => tarefa.finalizada);
}

const getFiltroTarefas = () => {
  const {filtro} = estado; 
  switch(filtro) {
    case 'pendentes':
      return getAtividadePendente();
    case 'finalizadas': 
      return getAtividadeFinalizada();
    default:
      return estado.tarefas;
  }
}
const addTarefa = ()=> {
  
  const novaTarefa = {
    titulo: estado.tarefaTemp, 
    finalizada: false
  }
  estado.tarefas.push(novaTarefa);
  estado.tarefaTemp = '';
}
</script>

<template>


<main class="container">
  
<Cabecalho :tarefas-pendentes="getAtividadePendente().length" />
<Formulario :add-tarefa="addTarefa" :estado-tarefa="estado.tarefaTemp" 
:nova-tarefa="novaTarefa => estado.tarefaTemp = novaTarefa.target.value" 
:estado-filtro="filtro => estado.filtro = filtro.target.value"/>

<ListaDeTarefas :get-tarefas-filtradas="getFiltroTarefas()" /> 


</main>
</template>

<style scoped>

</style>
