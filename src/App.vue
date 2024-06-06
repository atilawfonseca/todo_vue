<script setup>

import {reactive} from 'vue';

const estado = reactive({
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


</script>

<template>
<header>
  <div class="container">
    <div class="mt-4 p-3 bg-light rounded-4">
      <h1 class="mb-3">Tarefas</h1>
      <p >
        Você tem 7 atividades pendentes.
      </p>
    </div>
  </div>
</header>

<main class="container">
  <form class="mt-5">
    <div class="row">
      <div class="col-md-8">
        <input type="text" placeholder="Digite sua tarefa" class="form-control">
      </div>
      <div class="col-2">
        <select class="form-control" >
          <option value="todos">Todos</option>
          <option value="pendentes">Pendentes</option>
          <option value="finalizadas">Finalizadas</option>
        </select>
      </div>
      <div class="col-1">
        <button type="submit" class="btn btn-primary">Cadastrar</button>
      </div>
    </div>
  </form>

  <ul class="list-group">
    <li class="list-group-item mt-4" v-for="tarefa in estado.tarefas">
      
    </li>
  </ul>
</main>
</template>

<style scoped>

</style>
