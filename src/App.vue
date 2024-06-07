<script setup>

import {reactive} from 'vue';

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
<header>
  <div class="container">
    <div class="mt-4 p-3 bg-light rounded-4">
      <h1 class="mb-3">Tarefas</h1>
      <p >
        Você tem {{getAtividadePendente().length}} atividades pendentes.
      </p>
    </div>
  </div>
</header>

<main class="container">
  <form class="mt-5" @submit.prevent="addTarefa()">
    <div class="row">
      <div class="col-md-8">
        <input :value="estado.tarefaTemp" required type="text" placeholder="Digite sua tarefa" class="form-control" @change="novaTarefa => estado.tarefaTemp = novaTarefa.target.value">
      </div>
      <div class="col-1">
        <button type="submit" class="btn btn-primary">Cadastrar</button>
      </div>
      <div class="col-2">
        <select class="form-control" @change="filtro => estado.filtro = filtro.target.value">
          <option value="todos">Todos</option>
          <option value="pendentes">Pendentes</option>
          <option value="finalizadas">Finalizadas</option>
        </select>
      </div>
    </div>
  </form>

  <ul class="list-group">
    <li class="list-group-item mt-4" v-for="tarefa in getFiltroTarefas()">
      <input @change="concluido => tarefa.finalizada = concluido.target.checked" type="checkbox" :id="tarefa.titulo" :checked="tarefa.finalizada">
      <label :class="{done: tarefa.finalizada}" class="ms-3" :for="tarefa.titulo"> {{tarefa.titulo}}</label>
    </li>
  </ul>

</main>
</template>

<style scoped>
.done {
  text-decoration: line-through;
}
</style>
