<template>
    <div id="header">
        <a class="navbar-brand" href="">Todo</a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>
    </div>
</template>

<script>

    export default {
        name: "Header",
        components :{

        },
        data() {
            return {
                msg: "Todo List"
            }
        }
    }
</script>

<style scoped>
    a{
        color: #fff;
        text-decoration: none;
    }
</style>