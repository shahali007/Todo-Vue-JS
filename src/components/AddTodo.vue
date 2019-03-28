<template>
  <form class v-on:submit="addTodo">
    <div class="input-group mb-3">
      <input type="text" class="form-control" placeholder="Enter new item" v-model="title">
      <div class="input-group-append">
        <button class="btn btn-outline-secondary" type="submit" id="button-addon2">Add</button>
      </div>
    </div>
  </form>
</template>

<script>
export default {
  name: "AddTodo",
  data() {
    return {
      title: "",
      error: ""
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      const uuidv4 = require("uuid/v4");
      const newTodo = {
        id: uuidv4(),
        title: this.title,
        completed: true
      };
      //alert(newTodo.id);
      if (this.title !== "") {
        this.$emit("add-todo", newTodo);
        this.title = "";
        console.log("New item added : " + newTodo.title);
      } else {
        //alert("Field is required!"),
        this.error = "Field is required";
        this.$emit("ErrTodo", this.error);

        //console.log(this.error);
      }
    }
  }
};
</script>

<style scoped>
</style>