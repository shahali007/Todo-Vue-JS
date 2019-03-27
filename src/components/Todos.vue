<template>
  <div>
    <ul class="text-left">
        <li v-for="todo in todos" v-bind:key="todo.id">
            <TodoItem v-bind:todo="todo" v-on:delete="$emit('delete', todo.id)"/>
        </li>
    </ul>
  </div>
</template>

<script>
import TodoItem from './TodoItem';
export default {
  name: 'Todos',
  props : ["todos"],
  components :{
      TodoItem
  }
}
</script>

<style scoped>
    .text-left{
        text-align: left;
    }
    ul{
        list-style-type: none;
        padding: 0;
    }
    li{
        padding: 10px;
        border-bottom: 1px solid #fff;
        background: #f7f7f7;
        color: black;
    }
</style>
