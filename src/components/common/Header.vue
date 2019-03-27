<template>
    <div id="header">
        <a href="">{{ msg }}</a>
    </div>
</template>

<script>
    export default {
        name: "Header",
        data() {
            return {
                msg: "Todo List"
            }
        }
    }
</script>

<style scoped>
    #header {
        background: #fafafa;
        color: #000;
        text-align: center;
        padding: 15px;
    }
</style>