<template>
    <div class = 'task'>
        <h3 :class = "[task.completed ? 'task-text-completed':'task-text']">
            {{ task.text }}
        </h3>
        <div v-if = "task.completed" >
                <el-button @click = "completeTask(task.id)" type="success" icon="el-icon-check" disabled></el-button>
                <el-button @click = "deleteTask(task.id)" type="danger" icon="el-icon-delete"></el-button>
        </div>
        <div v-else>
                <el-button @click = "completeTask(task.id)" type="success" icon="el-icon-check"></el-button>
                <el-button @click = "deleteTask(task.id)" type="danger" icon="el-icon-delete"></el-button>
        </div>
    </div>
</template>

<script>

export default {
    name:'Task',
    props:{
        task:Object
    },
    methods: {
        deleteTask(id) {
            this.$emit('delete-task',id);
        },
        completeTask(id) {
            this.$emit('complete-task',id);
        }
    }
}
</script>

<style scoped>
.task {
    cursor: pointer;
    border: 1px solid black;
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 4px auto;
    color: rgb(18, 19, 19);
    background: rgb(5, 247, 255);
    padding: 14px 32px 14px 16px;
    border-radius: 5px;
    width: 90%;
}
.task-text {
    font-family:Arial, Helvetica, sans-serif
}
.task-text-completed {
    font-family:Arial, Helvetica, sans-serif;
    text-decoration: line-through;
    color: grey;
    opacity: 0.4;
}
</style>