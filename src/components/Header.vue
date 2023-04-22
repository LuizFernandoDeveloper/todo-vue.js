<script setup>
    const props = defineProps(['taskPending'])
</script>
<template>
    <header class="p-5 mb-4 mt-4 bg-light rounded-5 text-center">
        <h1>Minhas tarefas</h1>
        <p>
            Você possui <span class="text-primary">{{ props.taskPending }}</span> tarefas pendentes
        </p>
    </header>
</template>