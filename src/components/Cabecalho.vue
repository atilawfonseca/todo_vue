<script setup>
    const props = defineProps(['tarefasPendentes']);
</script>

<template>
    <header>
        <div class="container">
            <div class="mt-4 p-3 bg-light rounded-4">
                <h1 class="mb-3">Tarefas</h1>
                <p >
                    Você tem {{props.tarefasPendentes}} atividades pendentes.
                </p>
            </div>
        </div>
    </header>
</template>