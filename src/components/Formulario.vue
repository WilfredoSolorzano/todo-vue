<script setup>
  const props=defineProps(['cadastraTarefa','tarefasTemp','trocarFiltro','editaTarefaTemp']);
</script>

<template>
  <form @submit.prevent="props.cadastraTarefa" class="my-form">
    <div class="row">
      <div class="col">
        <input required :value="props.tarefasTemp" @change="props.editaTarefaTemp" type="text" placeholder="Digite aqui a descripção da tarefa" class="form-control">
      </div>
      <div class="col-md-2">
        <button type="submit" class="btn btn-primary">Cadastrar</button>
      </div>
      <div class="col-md-2">
        <select @change="props.trocarFiltro" class="form-control">
          <option value="todas">Todas las tareas</option>
          <option value="Pendente">Tareas Pendientes</option>
          <option value="finalizadas">Tareas Finalizadas</option>
        </select>
      </div>
    </div>
  </form>
</template>

<style scoped>
.my-form {
  background-color: #caa2a2; /* Cambiar color de fondo del formulario */
  padding: 20px;
  border-radius: 8px;
}
</style>