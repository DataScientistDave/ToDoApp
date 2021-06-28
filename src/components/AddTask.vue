<template>
    <div class = "add-task">
        <el-form>
            <el-input type = "text" v-model = "text" placeholder="Enter Task">
            </el-input>
        </el-form>
        <div class = "add-button">
            <Button @click = "submitTask"/>
        </div>
    </div>
</template>

<script>

import Button from './Button'

export default {
    name: 'AddTask',
    components : {
        Button
    },
    data() {
        return {
            text: ''
        }
    },
    methods: {
        submitTask(e) {
            e.preventDefault()
            
            if (!this.text) {
                alert('Please add a task!');
                return
            }
            
            const newTask = {
                id:Math.floor(Math.random() * 1000),
                text:this.text,
                completed:false
            }

            //Empty data value
            this.text = "";

            this.$emit('add-task',newTask); 
        }
    }
}
</script>

<style scoped>
.add-task {
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    padding-bottom: 20px;
}
.add-button {
    padding-left : 15px;
}
</style>