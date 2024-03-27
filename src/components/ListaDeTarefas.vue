<script setup>
    const props = defineProps(['tarefas']);

    function listaTemElementos() {
        if (props.tarefas.length > 0) {
            return true;
        } else {
            return false;
        }
    }
</script>

<template>
    <ul v-if="listaTemElementos()" class="list-group mt-4">
        <li class="list-group-item" v-for="tarefa in props.tarefas">
            <input @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada"
                :id="tarefa.titulo" type="checkbox">
            <label :class="{ done: tarefa.finalizada }" class="ms-3" :for="tarefa.titulo">
                {{ tarefa.titulo }}
            </label>
        </li>
    </ul>
    <!--<h1>{{ tarefa.length }}</h1>-->
    <p class="mt-4" v-else>Não há elementos na lista</p>
</template>

<style scoped>
    .done {
        text-decoration: line-through;
    }
</style>