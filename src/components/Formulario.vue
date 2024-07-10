<template>
    <form @submit.prevent="cadastraTarefa">
      <div class="row">
        <div class="col">
          <input required :value="estado.tarefasTemporarias" @change="evento => estado.tarefasTemporarias=evento.target.value" type="text" placeholder="Digite aqui a descripção da tarefa" class="form-control">
        </div>
        <div class="col-md-2">
          <button type="submit" class="btn btn-primary">Cadastrar</button>
        </div>
        <div class="col-md-2">
          <select @change="evento => estado.filtro=evento.target.value" class="form-control">
            <option value="todas">Todas las tarefas</option>
            <option value="Pendente">Tarefas Pendientes</option>
            <option value="finalizadas">Tarefas Finalizadas</option>
          </select>
        </div>
      </div>
    </form>
</template>