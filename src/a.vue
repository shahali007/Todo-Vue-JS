<template>
    <div id="app">
        <div id="nav">
            <router-link to="/">Home</router-link> |
            <router-link to="/about">About</router-link>
        </div>
        <router-view/>
 
        <nav class="navbar navbar-expand-lg navbar-light bg-light fixed-top shadow-lg">
            <Header/>
            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <AddTodo v-on:add-todo="addTodo" v-on:ErrTodo="updateError($event)"/>
            </div>
        </nav>

        <div class="container">
            <div class="row">
                <div class="col-sm-2"></div>
                <div class="col-sm-8">

                    <div v-if="todos.length">
                        <div class="btn-group w-100 mb-4">
                            <button type="button" class="btn btn-outline-secondary" disabled>Total item : {{ todos.length }}</button>
                            <button type="button" class="btn btn-outline-secondary" disabled>Completed : {{ CompltedTodos.length }}</button>
                            <button type="button" class="btn btn-outline-secondary" disabled>Not Completed : {{ NotCompltedTodos.length }}</button>
                        </div>

                        <div v-if="this.error" class="alert alert-warning alert-dismissible fade show" role="alert">
                            <strong>{{ error }}</strong>
                        </div>
                        <Todos v-bind:todos="todos" v-on:delete="deleteTodo"/>
                    </div>
                    <div v-else class="not-found">
                        <h3>No item found!</h3>
                        <img src="https://mednear.com/assets/web/images/icons/empty-product.png" alt="Data Not Found!" style="width:300px;margin:auto;">
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

    import Header from './components/common/Header';
    import Todos from './components/Todos';
    import AddTodo from './components/AddTodo';
    import axios from 'axios'

    export default {
        name: 'app',
        components: {
            Header,
            Todos,
            AddTodo
        },
        data() {
            return {
                todos: [],
                error : ''
            }
        },

        methods: {
            deleteTodo(id) {
                // alert("Hello Brother. Your ID is : "+ id);
                this.todos = this.todos.filter(todo => todo.id !== id);
            },
            addTodo(newTodo){
                this.todos = [...this.todos, newTodo]
                this.error = '';
            },
            updateError(err){
                this.error = err;
                console.log(this.error);
            }
        },
        computed : {
            CompltedTodos : function () {
                return this.todos.filter(function(data) {
                    return !data.completed;
                });
            },
            NotCompltedTodos : function () {
                return this.todos.filter(function(data) {
                    return data.completed;
                });
            }
        },
        created(){
            axios.get('https://jsonplaceholder.typicode.com/todos?_limit=40')
                .then(res => this.todos = res.data)
                .catch(err => console.log(err))
        },
    }
</script>

<style>
    body {
        padding-top: 100px;
    }

    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin: auto;
    }

    .not-found {
        margin-top: 100px;
    }
</style>
