<template>
    <form class="form-inline ml-auto my-2 my-lg-0" v-on:submit="addTodo">
        <input class="form-control mr-sm-2" v-model="title" type="text" placeholder="Enter">
        <button class="btn btn-outline-secondary my-2 my-sm-0" type="submit">Add</button>
    </form>
</template>

<script>
    export default {
        name: "AddTodo",
        data(){
            return{
                title : ''
            }
        },
        methods : {
            addTodo(e){
                e.preventDefault();
                const uuidv4 = require('uuid/v4');
                const newTodo = {
                    id : uuidv4(),
                    title : this.title,
                    completed : true
                };
                //alert(newTodo.id);
                if(this.title !== ''){
                    this.$emit('add-todo', newTodo);
                    this.title = '';
                    console.log("New item added : " + newTodo.title)
                }
                else{
                    alert("Field is required!")
                }
            }
        }
    }
</script>

<style scoped>

</style>