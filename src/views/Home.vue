<template>
    <div>
        <AddTodo @add-todo="addTodoHandler"/>
        <Todos 
            v-bind:todos="todos" 
            v-on:delete-todo="deleteTodoHandler" 
            v-on:done-task="completeUpSender"
        />
    </div>
</template>

<script>
    import Todos from '../components/Todos';
    import AddTodo from '../components/AddTodo';
    // import axios from 'axios';

    export default {
        name: 'App',
        components: { 
            //we using like component wrapper. that contain all the conponent and serve into parent component.
            Todos,
            AddTodo,
        },
        props:{
            todos:Array,
            completed_list:Array
        },
        methods:{
            deleteTodoHandler : function(todo_id){
                this.$emit('delete-task',todo_id);
            },
            completeUpSender : function(operation_item){
                this.$emit('done-task',operation_item);
            },
            addTodoHandler : function(newItem){
                this.$emit('add-task',newItem);
            },
        },
    }
</script>

<style>
    /* common button */
    .btn{
        border-radius: 50%;
        background-color: #fff;
        border:none;
        margin-right: 10px;
        outline: 0;
        transition: 0.3s;
        cursor: pointer;
        height: 40px;
        width: 40px;
    }
</style>
