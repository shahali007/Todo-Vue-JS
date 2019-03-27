<template>
  <div id="app">
    <Header/>
    <div v-if="!todos.length" class="not-found">
      <h3>No item found!</h3>
      <img src="https://mednear.com/assets/web/images/icons/empty-product.png" alt="" style="width:300px;margin:auto;">
    </div>
    <div>
      <Todos v-bind:todos="todos" v-on:delete="deleteTodo"/>
    </div>
  </div>
</template>

<script>
  import Todos from './components/Todos';
  import Header from './components/common/Header';
  export default {
    name: 'app',
    components: {
        Header,
        Todos
    },
    data(){
      return{
        todos : [
          {
              id : 1,
              title : "Shahnaz Rahmatullah passes away",
              completed : true
          },
          {
              id : 2,
              title : "Ducsu finally gets going",
              completed : true
          },
          {
              id : 3,
              title : "Fire guts several shops in Lalbagh",
              completed : true
          },
          {
              id : 4,
              title : "Voting to 117 upazila parishads underway",
              completed : true
          },
          {
              id : 5,
              title : "Thailand votes in face-off between coup leader and 'democratic front'",
              completed : true
          }
        ]
      }
    },
    methods : {
      deleteTodo(id){
        // alert("Hello fazil. Tor id hocche : "+ id);
        this.todos = this.todos.filter(todo => todo.id !== id);
      }
    }
  }
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  max-width:500px;
  margin: auto;
}
.not-found{
  margin-top: 150px;
}
</style>
