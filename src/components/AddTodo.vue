<template>
    <div class="add-todo-container">
        <form @submit.prevent="addTodoHandler">
            <div class="form-structure">
                <input type="text" name="title" v-model="title" placeholder="add task..."  required/>
                <div>
                    <button type="submit" class="btn add-btn">
                        <img src="/img/plus.svg" height="20px" width="20px"/>
                    </button>
                </div>
            </div>
        </form>
    </div>
</template>

<script>

    // import { v4 as uuidv4 } from 'uuid';

    export default {
        name:'AddTodo',
        data(){
            return {
                title:''
            }
        },
        methods:{
            addTodoHandler: function name() {
                const newItem = {
                    // id:uuidv4(),
                    title:this.title,
                    completed:false
                }
                this.$emit('add-todo',newItem);
                this.title = ""
            }
        }
    }
</script>

<style scoped>
    .add-todo-container{
        box-shadow: 0 0 10px 10px rgba(0,0,0,0.12);
        padding:20px;
        border-radius: 10px;
        width: 28vw;
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 30px;
        background: linear-gradient(to right, #00F260, #0575E6);
    }
    .form-structure{
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
    input[type='text']{
        font-weight: 600;
        border: 0;
        border-radius: 3px;
        font-size: 20px;
        outline: 0;
        padding: 8px 15px;
        width: 15vw;
        transition: 0.3s;
    }
    input[type='text']:focus{
        transition: 0.3s;
        box-shadow: 0 3px 3px 3px rgba(0,0,0,0.1);
    }
    form{
        width: 100%;
    }
    .add-btn:hover{
        transition: 0.3s;
        box-shadow: 0 0 5px 5px rgba(0, 240, 96, 0.62);
    }
</style>