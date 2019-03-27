<template>
    <div>
        <label v-bind:for="'item-'+todo.id">
            <input type="checkbox" v-on:change="markComplete" v-bind:id="'item-'+todo.id">
            <span class="truncate" v-bind:class="{'is-complete': !todo.completed}">{{ todo.title }}</span>
            <button v-if="!todo.completed" v-bind:disabled="todo.completed" v-on:click="$emit('delete', todo.id)" class="close">x</button>
        </label>
    </div>
</template>

<script>
export default {
    name : 'TodoItem',
    props : ["todo"],
    methods : {
        markComplete(){
            this.todo.completed = !this.todo.completed;
        }
    }
}
</script>

<style scoped>
    .is-complete{
        text-decoration: line-through;
    }
    .close{
        border: none;
        background: #eeeeee;
        color: #000;
        padding: 13px 15px;
        float: right;
        cursor: pointer;
        margin-top: -10px;
    }
    .close:hover{
        background: red;
        color: #fff;
    }
    .close[disabled]:hover{
        cursor: not-allowed;
        background: #eeeeee;
        color: #000;
    }
    .truncate{
        width: 80%;
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
        display: inline-block;
    }
</style>


