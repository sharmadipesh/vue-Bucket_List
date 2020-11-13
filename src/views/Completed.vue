<template>
    <div>
        <div v-for="task in completed_list" :key="task.id">
            <div class="card-style completed-card-style">
                {{task.id}}.  {{task.title}}
            </div>
        </div>

    </div>
</template>

<script>
    export default {
        name:'Completed',
        props:{
            completed_list:Array
        }
    }
</script>

<style scoped>
    .completed-card-style{
        background: linear-gradient(to right,#ee0979,#ff6a00);
        padding: 15px;
        color: #fff;
        font-weight: 900;
        font-style: italic;
        font-size: 20px;
    }
</style>