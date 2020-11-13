<template>
    <div>
        <div v-for="todo in todos" :key="todo.id">
            <TodoItem :todo='todo' v-on:delete-todo="$emit('delete-todo',todo.id)" v-on:done-task="$emit('done-task',todo)"/>
        </div>
    </div>
</template>

<script>

    import TodoItem from './TodoItem';

    export default {
        name:'Todos',   //name of component,
        // props:['todos'],
        props:{
            todos:Array
        },
        components:{
            TodoItem,
        }
    }
</script>

<style scoped>

</style>