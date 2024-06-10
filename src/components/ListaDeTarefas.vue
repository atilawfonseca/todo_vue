<script setup>
const props = defineProps(['getTarefasFiltradas', 'TarefasConcluidas'])
</script>

<template>
    <ul class="list-group">
        <li class="list-group-item mt-4" v-for="tarefa in props.getTarefasFiltradas">
            <input @change="concluido => tarefa.finalizada = concluido.target.checked" type="checkbox" :id="tarefa.titulo" :checked="tarefa.finalizada">
            <label :class="{done: tarefa.finalizada}" class="ms-3" :for="tarefa.titulo"> {{tarefa.titulo}}</label>
        </li>
    </ul>
</template>
<style scoped>
.done {
  text-decoration: line-through;
}
</style>