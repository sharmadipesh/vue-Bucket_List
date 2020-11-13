<template>
    <div class="home-links">
        <div id="nav">
            <router-link to="/" class="remain">Remaining</router-link>|
            <router-link to="/completed">Completed</router-link>
        </div>
        <router-view 
            v-bind:completed_list="completed_list"
            v-bind:todos="todos"
            @done-task="completedTaskHandler" 
            v-on:delete-task='deleteTodoHandler' 
            v-on:add-task='addTodoHandler' 
        >
        </router-view>
    </div>
</template>

<script>
    // v-on:done-task='completeHandler'
    import axios from 'axios';

    export default {
        name:'HomeLayout',
        data(){
            return {
                todos:[],
                completed_list:[]
            }
        },
        methods:{
            deleteTodoHandler : function(todo_id){
                axios.delete(`https://jsonplaceholder.typicode.com/todos/${todo_id}`)
                .then(() => {
                    this.todos = this.todos.filter(todo => todo.id !== todo_id)
                })
                .catch(error => {
                    console.log(error);
                })
            },
            addTodoHandler : function(newItem){
                let {title,completed} = newItem;
                axios.post('https://jsonplaceholder.typicode.com/todos',{title,completed})
                .then(response => {
                    this.todos = [...this.todos,response.data];
                })
                .catch(error => {
                    console.log(error);
                })
            },
            completedTaskHandler : function(operation_item){
                this.deleteTodoHandler(operation_item.id)
                this.completed_list = [...this.completed_list,operation_item]
            } 
        },
        created(){
            axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
                .then(response => {
                    // this.todos = [...response.data]
                    const completed_task = response.data.filter((task) => task.completed)
                    const remainig_tasks = response.data.filter((task) => !task.completed)
                    this.completed_list = [...completed_task];
                    this.todos = [...remainig_tasks];
                })
                .catch(error => {
                    console.log(error);
                })
        }
    }
</script>

<style scoped>
    #nav{
        margin-bottom: 20px;
        text-align: center;
    }
    #nav .remain{
        margin-right: 5px;
    }
</style>