<script setup>
defineProps({ tarefas: Array });
</script>

<template>
    <ul class="list-group mt-4">
        <li class="list-group-item" v-for="(tarefa, index) in tarefas" :key="index">
            <input @change="evento => tarefa.finalizada = evento.target.checked" :id="'tarefa-' + index"
                type="checkbox">
            <label :class="{ done: tarefa.finalizada }" class="ms-3" :for="'tarefa-' + index">
                {{ tarefa.titulo }}
            </label>
        </li>
    </ul>
</template>

<style scoped>
.done {
    text-decoration: line-through;
}
</style>
