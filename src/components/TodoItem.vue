<template>
    <div class="card-container card-style" :class="{'is-completed':todo.completed}">
        <div class="card-part-one">
            <!-- <input type="checkbox" v-on:change="markComplete"> -->
            <label class="container">
                <input type="checkbox" :checked="todo.completed" v-on:change="markComplete(todo)" >
                <span class="checkmark"></span>
            </label>
            <div class="todo-title" :title="todo.title">{{todo.title}}</div>
        </div>
        <div>
            <button class="btn delete-btn" @click="$emit('delete-todo',todo.id)">
                <img src="/img/trash.svg" height="20px" width="20px"/>
            </button>
        </div>
    </div>
</template>

<script>
    export default {
        name:'TodoItem',
        props:{
            todo:Object
        },
        methods:{
            markComplete:function(operation_item) {
                this.todo.completed = ! this.todo.completed;
                this.$emit('done-task',operation_item);
            }
        }
    }
</script>

<style scoped>
    .card-container{
        background: linear-gradient(to right, #00F260, #0575E6);
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    .card-part-one{
        display: flex;
        align-items: center;
    }
    .todo-title{
        font-weight: 600;
        margin-left: 10px;

        /* ellipsis */
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
        /* width: 300px; */
        width: 15vw;
    }
    .is-completed{
        text-decoration: line-through;
        text-decoration-color: red;
        text-decoration-thickness: 20px;
    }

    .delete-btn:hover{
        transition: 0.3s;
        box-shadow: 0 0 8px 8px rgba(255, 97, 110, 0.62);
    }

    /* checkbox */
    /* The container */
        .container {
            display: block;
            position: relative;
            padding-left: 35px;
            margin-bottom: 28px;
            cursor: pointer;
            font-size: 22px;
            -webkit-user-select: none;
            -moz-user-select: none;
            -ms-user-select: none;
            user-select: none;
        }

        /* Hide the browser's default checkbox */
        .container input {
            position: absolute;
            opacity: 0;
            cursor: pointer;
            height: 0;
            width: 0;
        }

        /* Create a custom checkbox */
        .checkmark {
            position: absolute;
            top: 0;
            left: 0;
            height: 25px;
            width: 25px;
            background-color: #fff;
            border-radius: 5px;
            transition: 0.3s;
        }

        /* On mouse-over, add a grey background color */
        .container:hover input ~ .checkmark {
            /* background-color: #ccc;      */
            box-shadow: 0 3px 3px 3px rgba(0,0,0,0.1);
            transition: 0.3s;
            
        }

        /* When the checkbox is checked, add a blue background */
        .container input:checked ~ .checkmark {
            background-color: #0575E6;
        }
        /* Create the checkmark/indicator (hidden when not checked) */
        .checkmark:after {
            content: "";
            position: absolute;
            display: none;
        }

        /* Show the checkmark when checked */
        .container input:checked ~ .checkmark:after {
            display: block;
        }

        /* Style the checkmark/indicator */
        .container .checkmark:after {
            left: 9px;
            top: 5px;
            width: 5px;
            height: 10px;
            border: solid white;
            border-width: 0 3px 3px 0;
            -webkit-transform: rotate(45deg);
            -ms-transform: rotate(45deg);
            transform: rotate(45deg);
        }
</style>