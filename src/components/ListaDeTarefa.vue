<script setup>
  const props=defineProps(['tarefas']);
</script>

<template>
  <ul class="list-group mt-4 styled-list">
    <li class="list-group-item styled-item" v-for="tarefa in props.tarefas" :key="tarefa.titulo">
      <input @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada" :id="tarefa.titulo" type="checkbox">
      <label :class="{ done: tarefa.finalizada }" class="ms-3" :for="tarefa.titulo">
        {{ tarefa.titulo }}
      </label>
    </li>
  </ul>
  <p v-if="props.tarefas.length > 0 && props.tarefas.every(t => t.finalizada)" style="color: orange; font-weight: bold;">
    Não existem tarefas pendentes
  </p>
</template>

<style scoped>
.styled-list {
  background-color: #caa2a2; 
  border: 1px solid #eb8cc6; 
  border-radius: 8px; 
  padding: 10px; 
}
.styled-item {
  padding: 10px; 
  background-color: #b4abab; 
}
.styled-item:last-child {
  border-bottom: none;
}
.done {
  text-decoration: line-through;
}
</style>