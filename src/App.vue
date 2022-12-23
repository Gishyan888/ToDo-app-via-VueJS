<template>
    <div class="container">
        <h1 class="todoTitle">ToDo App</h1>
        <div class="content">
            <input v-model="title" @input="inputTitle()" type='text' placeholder='What do you have planned?' />
        </div>
        <button @click="createTask" class="btn">Add Task</button>
    </div>

    <h1 class="taskTitle">Tasks</h1>
    <div class="mainContainer">
        <div v-for="task in tasks" :key="task.id" class="itemContainer">
            <p>{{ task.title }}</p>
            <button @click="deleteTask(task.id)" class="deletebtn">Delete Task</button>
        </div>
    </div>
</template>

<script>

export default {
    data() {
        return {
            tasks: [],
            title: ''
        }
    },
    methods: {
        createTask() {
            let newTask = {
                id: Math.random(),
                title: this.title
            }
            this.tasks.push(newTask)
            this.title = ""
        },
        deleteTask(id){
            let updateTasks = this.tasks.filter((el) => el.id !== id);
            this.tasks = updateTasks;
        }
    }
}
</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}


.container {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.todoTitle {
    font-size: 50px;
    color: #ff0080;
    text-align: center;
}

.content {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: auto;
}

.content input {
    width: 30%;
    height: 40px;
    border-radius: 10px;
    border: none !important;
    background: #111827;
    color: #ff0080;
    font-size: 20px;
    padding: 0 20px;
}

.btn {

    width: 10%;
    height: 40px;
    border-radius: 10px;
    background: linear-gradient(#ff0080, #4c00ff);
    font-size: 1.5vw;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    margin-top: 1vh;
    transition: .3s linear;
    cursor: pointer;
}

.content button:hover {
    transform: scale(1.1);
}
.deletebtn{
    width: 35%;
    border-radius: 10px;
    font-size: 1.5vw;   
    border: none;
    transition: .3s linear;
    cursor: pointer;
}
.deletebtn:hover{
    background: linear-gradient(#ff0080, #4c00ff);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
}


.taskTitle {
    font-size: 50px;
    color: #ff0080;
    text-align: center;
    font-weight: 100;
}

.mainContainer {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    flex-wrap: nowrap;
}

.itemContainer {
    width: 30%;
    height: 40px;
    border-radius: 10px;
    border: none !important;
    background: #111827;
    color: #ff0080;
    font-size: 25px;
    padding: 5px 20px;
    margin-top: 1vh;
    display: flex;
    justify-content: space-between;
}
</style>