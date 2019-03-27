<template>
    <div class="hello">
        <h1>Welcome to vue ToDo project!</h1>
    </div>
</template>

<script>
    export default {
        name: 'HelloWorld',
        props: {
            msg: String
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
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    h3 {
        margin: 40px 0 0;
    }

    ul {
        list-style-type: none;
        padding: 0;
    }

    li {
        display: inline-block;
        margin: 0 10px;
    }

    a {
        color: #42b983;
    }
</style>
