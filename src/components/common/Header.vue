<template>
    <div id="header">
        <nav class="navbar navbar-expand-lg navbar-light bg-light fixed-top shadow-lg">
            <router-link to="/" class="navbar-brand" >Todo</router-link>
            <ul class="navbar-nav mr-auto" id="nav">
                <li class="nav-item"><router-link to="/" class="nav-link">Home </router-link> </li>
                <li class="nav-item"><router-link to="/about" class="nav-link">About </router-link></li>
            </ul>
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <AddTodo v-bind:addTodo="$emit('add-todo')" v-on:ErrTodo="$emit('ErrTodo')"/>
            </div>
        </nav>
    </div>
</template>

<script>
    import AddTodo from '../AddTodo';
    export default {
        name: "Header",
        components :{
            AddTodo
        },
        data() {
            return {
               
            }
        }
    }
</script>

<style scoped>
    a{
    
        text-decoration: none;
    }
</style>