<script setup>
const props = defineProps(['registerTask', 'taskTemp' , 'toChangeFilter', 'editTaskTemp']);
</script>
<template>
    <form @submit.prevent="props.registerTask">
        <div class="row">
            <div class="col">
                <input :value="props.taskTemp" @change="props.editTaskTemp" required
                    type="text" placeholder="Digite aqui o nome da tarefa" class="form-control" />
            </div>
            <div class="col-md-2">
                <button type="submit" class="btn btn-primary">Cadastra</button>
            </div>
            <div class="col-md-3 text-center">
                <select @change="props.toChangeFilter" class="form-control">
                    <option value="todas">Todos as tarefas</option>
                    <option value="Pendentes">Pendentes</option>
                    <option value="Finalizadas">Finalizadas</option>
                </select>
            </div>
        </div>
    </form>
</template>
