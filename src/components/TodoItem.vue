<template>
    <div>
        <div class="custom-control custom-checkbox">
            <input type="checkbox" :checked="!todo.completed" class="custom-control-input" v-bind:id="'item-'+todo.id" v-on:change="markComplete">
            <label v-bind:for="'item-'+todo.id" class="custom-control-label" v-bind:class="{'is-complete': !todo.completed}">
                <span class="truncate">{{ todo.title }}</span>
            </label>
            <button v-if="!todo.completed" v-bind:disabled="todo.completed" v-on:click="$emit('delete', todo.id)" class="btn text-danger font-weight-bold border-0 shadow-0 bg-white btn-sm float-right">&#128465;</button>
        </div>
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
    label{
        width: calc(100% - 30px);
        cursor: pointer;
    }
    .truncate{
        width: 80%;
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
    }
</style>


