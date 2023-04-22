<script setup>
  import { reactive } from 'vue';
  import Header from './components/Header.vue';
  import Form from './components/Form.vue';
  import ListTask from './components/ListTask.vue' 
  const state  = reactive({
    filter: "todas",
    taskTemp:'',
    task:[],
  });

  const getTaskPending = () => {
    return state.task.filter(task => !task.stateOfTask);
  };

  const getTaskFinished = () => {
    return state.task.filter(task => task.stateOfTask);
  };

  const getTaskFilter = () => {
    const {filter} = state;
    switch(filter){
      case 'Pendentes':
        return getTaskPending();
      case 'Finalizadas':
        return getTaskFinished();
      default:
        return state.task;
    };
  };

  const registerTask = () => {

    const newTask = {
      title: state.taskTemp,
      stateOfTask: false
    }
    state.task.push(newTask);
    state.taskTemp = '';
  }
</script>

<template>
  <div class="container">
    <Header v-bind:task-pending="getTaskPending().length"></Header>
    <Form 
    :register-task="registerTask"
    :task-temp="state.taskTemp" 
    :edit-task-temp="event => state.taskTemp = event.target.value" 
    :to-change-filter="event => state.filter = event.target.value"></Form>
    <ListTask :task="getTaskFilter()"></ListTask> 
  </div>
</template>

<style scoped>
.del{
  text-decoration: line-through;
}
</style>
