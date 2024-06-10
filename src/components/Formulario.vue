<script setup>
const props = defineProps(['addTarefa', 'estadoTarefa', 'novaTarefa', 'estadoFiltro'])
</script>

<template>
    <form class="mt-5" @submit.prevent="props.addTarefa">
        <div class="row">
            <div class="col-md-8">
                <input :value="props.estadoTarefa" required type="text" placeholder="Digite sua tarefa" class="form-control" @change="props.novaTarefa">
            </div>
            <div class="col-1">
                <button type="submit" class="btn btn-primary">Cadastrar</button>
            </div>
            <div class="col-2">
                <select class="form-control" @change="props.estadoFiltro">
                <option value="todos">Todos</option>
                <option value="pendentes">Pendentes</option>
                <option value="finalizadas">Finalizadas</option>
                </select>
            </div>
        </div>
    </form>
</template>