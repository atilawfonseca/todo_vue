<script setup>

const props = defineProps(['getTarefasFiltradas', 'TarefasConcluidas'])

const messagemDeFinalizada = () => {
    const arrayTarefas = props.getTarefasFiltradas;
    const contador =  arrayTarefas.map(tarefa => {
        return tarefa.finalizada; 
    })
    return contador.every(item => item ===true) ;
}

</script>

<template>
    <ul  class="list-group">
        <li class="list-group-item mt-4" v-for="tarefa in props.getTarefasFiltradas">
            <input @change="concluido => tarefa.finalizada = concluido.target.checked" type="checkbox" :id="tarefa.titulo" :checked="tarefa.finalizada">
            <label :class="{done: tarefa.finalizada}" class="ms-3" :for="tarefa.titulo"> {{tarefa.titulo}}</label>
        </li>
    </ul>
    <ul v-if="messagemDeFinalizada()">
        <h3>Você não tem nenhuma tarefa pendente!</h3>
    </ul>
    


</template>
<style scoped>
.done {
  text-decoration: line-through;
}
ul h3 {
    text-align: center;
    margin-top: 1em;
}
</style>