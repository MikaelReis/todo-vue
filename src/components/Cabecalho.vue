<script setup>
defineProps({ tarefasPendentes: Number });
</script>

<template>
    <header class="p-5 mb-4 mt-4 bg-light rounded-3">
        <h1>Minhas tarefas</h1>
        <p>Você possui {{ tarefasPendentes }} tarefas pendentes</p>
    </header>
</template>


<style scoped>
.done {
    text-decoration: line-through;
}
</style>
