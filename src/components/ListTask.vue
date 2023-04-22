<script setup>
    const props =  defineProps(['task']);
</script>
<template>
    <ul class="list-group mt-4">
        <li class="list-group-item" v-for="task in props.task">
            <input @change="event => task.stateOfTask = event.target.checked" type="checkbox" :id="task.title"
                :checked="task.stateOfTask">
            <label :class="{ del: task.stateOfTask }" class="ms-3 " :for="task.title">{{ task.title }}</label>
        </li>
    </ul>
</template>