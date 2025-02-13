<script setup>
import { reactive } from 'vue';
import Cabecalho from './components/Cabecalho.vue';
import Formulario from './components/Formulario.vue';
import ListaDeTarefas from './components/ListaDeTarefas.vue';

const estado = reactive({
  filtro: 'todas',
  tarefaTemp: '',
  tarefas: [ 
    { titulo: 'Estudar ES6', finalizada: false },
    { titulo: 'Estudar SASS', finalizada: false },
    { titulo: 'Ir para academia', finalizada: true }
  ]
});

const getTarefasPendentes = () => estado.tarefas.filter(tarefa => !tarefa.finalizada);
const getTarefasFinalizadas = () => estado.tarefas.filter(tarefa => tarefa.finalizada);
const getTarefasFiltradas = () => {
  switch (estado.filtro) {
    case 'pendentes': return getTarefasPendentes();
    case 'finalizadas': return getTarefasFinalizadas();
    default: return estado.tarefas;
  }
};

const cadastraTarefa = (event) => {
  event.preventDefault();
  if (!estado.tarefaTemp.trim()) return;
  
  estado.tarefas.push({ titulo: estado.tarefaTemp, finalizada: false });
  estado.tarefaTemp = '';
};

const trocarFiltro = (evento) => {
  estado.filtro = evento.target.value;
};

const editaTarefaTemp = (evento) => {
  estado.tarefaTemp = evento.target.value;
};
</script>

<template>
  <div class="container">
    <Cabecalho :tarefasPendentes="getTarefasPendentes().length"/>
    <Formulario 
      :trocar-filtro="evento => estado.filtro = evento.target.value" 
      :tarefa-temp="estado.tarefaTemp" 
      :edita-tarefa-temp="evento => estado.tarefaTemp = evento.target.value" 
      :cadastra-tarefa="cadastraTarefa"
    />
    <ListaDeTarefas :tarefas="getTarefasFiltradas()"/>
  </div>
</template>






