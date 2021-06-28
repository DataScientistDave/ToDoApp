<template>
<div class = "tasks">
    <div :key = "task.id" v-for = "task in tasks">
        <Task :task = "task" @delete-task = "$emit('delete-task',task.id)" 
        @complete-task = "$emit('complete-task',task.id)"/>
    </div>
</div>
</template>

<script> 
import Task from './Task'

export default {
    name:'Tasks',
    components: {
        Task
    },
    props: {
        tasks: Array
    },
    emits: ['delete-task','complete-task','add-task'],
}
</script>

