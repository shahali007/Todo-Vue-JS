<template>
    <div id="app">
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
                        <Todos v-bind:todos="todos" v-on:delete="deleteTodo" v-on:add-todo="$emit('add-todo', addTodo)" v-on:ErrRodo="$emit('ErrTodo', updateError(event))"/>
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

    import Header from '../components/common/Header';
    import Todos from '../components/Todos';
    import axios from 'axios'

    export default {
        name: 'Home',
        components: {
            Header,
            Todos
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
                axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
                .then(res=> this.todos = this.todos.filter(todo => todo.id !== id))
                .catch(err => console.log(err));
            },
            addTodo(newTodo){
                const {id, title, completed} = newTodo;
                axios.post('https://jsonplaceholder.typicode.com/todos', {id, title, completed})
                     .then(res=> this.todos = [...this.todos, res.data])
                     .catch(err => console.log(err));
                this.error = '';
            },
            updateError(err){
                this.error = err;
                console.log(err);
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
            axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
                 .then(res => this.todos = res.data)
                 .catch(err => console.log(err))
        }
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
