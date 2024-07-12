<script setup>
import { reactive} from 'vue';
import Cabecalho from "./components/Cabecalho.vue";
import Formulario from "./components/Formulario.vue";
import ListaDeTarefa from "./components/ListaDeTarefa.vue";

const estado=reactive({
  filtro:'todas',
  tarefasTemp:"",
  tarefas:[
    {
      titulo:'Estudar ES6',
      finalizada:false,
    },
    {
      titulo:'Estudar SAS',
      finalizada:false,
    },
    {
      titulo:'Ir para a academia',
      finalizada:true,
    }
  ]
})
const getTarefasPendentes=()=> {
    return estado.tarefas.filter(tarefa => !tarefa.finalizada);
  }
  const getTarefasFinalizadas=()=> {
    return estado.tarefas.filter(tarefa => tarefa.finalizada);
  }
  const getTarefasFiltradas=() =>{
    const {filtro}=estado;
    switch(filtro){
      case 'Pendente':
        return getTarefasPendentes();
      case 'finalizadas':
        return getTarefasFinalizadas();
      default:
        return estado.tarefas
    }
  }
  const cadastraTarefa= () =>{
    const tarefaNova={
      titulo:estado.tarefasTemp,
      finalizada:false
    }
    estado.tarefas.push(tarefaNova);
    estado.tarefasTemp="";
  }
</script>

<template>
  <div class="container">
    <Cabecalho :tarefasPendentes="getTarefasPendentes().length" />
    <Formulario :trocarFiltro="evento=> estado.filtro=evento.target.value" :tarefasTemp="estado.tarefasTemp" :editaTarefaTemp="evento=>estado.tarefasTemp=evento.target.value" :cadastraTarefa="cadastraTarefa" />
  <ListaDeTarefa :tarefas="getTarefasFiltradas()" />
  </div>
</template>

