<template>
    <div id="app">
        <nav class="navbar navbar-expand-lg navbar-light bg-light fixed-top shadow-lg">
            <Header/>
            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <AddTodo v-on:add-todo="addTodo"/>
            </div>
        </nav>

        <div class="container">
            <div class="row">
                <div class="col-sm-2"></div>
                <div class="col-sm-8">
                    <div v-if="!todos.length" class="not-found">
                        <h3>No item found!</h3>
                        <img src="https://mednear.com/assets/web/images/icons/empty-product.png" alt=""
                             style="width:300px;margin:auto;">
                    </div>
                    <div>
                        <Todos v-bind:todos="todos" v-on:delete="deleteTodo"/>
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

    export default {
        name: 'app',
        components: {
            Header,
            Todos,
            AddTodo
        },
        data() {
            return {
                todos: [
                    {
                        id: 1,
                        title: "Shahnaz Rahmatullah passes away",
                        completed: true
                    },
                    {
                        id: 2,
                        title: "Ducsu finally gets going",
                        completed: true
                    },
                    {
                        id: 3,
                        title: "Fire guts several shops in Lalbagh",
                        completed: true
                    },
                    {
                        id: 4,
                        title: "Voting to 117 upazila parishads underway",
                        completed: true
                    },
                    {
                        id: 5,
                        title: "Thailand votes in face-off between coup leader and 'democratic front'",
                        completed: true
                    }
                ]
            }
        },
        methods: {
            deleteTodo(id) {
                // alert("Hello fazil. Tor id hocche : "+ id);
                this.todos = this.todos.filter(todo => todo.id !== id);
            },
            addTodo(newTodo){
                this.todos = [...this.todos, newTodo]
            }
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
        margin-top: 150px;
    }
</style>
