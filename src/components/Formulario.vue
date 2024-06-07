<template>
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
</template>