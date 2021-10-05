<template>
  <div class="container md pt-3">
    <h3 class="text-center">Todos</h3>
    <hr />
    <AddToDo @addToDo="addToDo($event)" />
    <hr />
    <Todo
      @deleteToDo="deleteToDo($event)"
      v-for="todo in todoList"
      :todo="todo"
      :key="todo.id"
    />
  </div>
</template>

<script>
import Todo from "@/components/Todo";
import AddToDo from "@/components/AddToDo";
import axios from "axios";
export default {
  components: { Todo, AddToDo },
  created() {
    axios
      .get("https://todos-70068-default-rtdb.firebaseio.com/todos.json")
      .then((response) => {
        console.log(response.data);
        for (let key in response.data) {
          this.todoList.push({ id: key, text: response.data[key].text });
        }
      })
      .catch((e) => console.log(e));
  },
  methods: {
    addToDo(value) {
      axios
        .post("https://todos-70068-default-rtdb.firebaseio.com/todos.json", {
          text: value,
        })
        .then((response) => {
          this.todoList.push({ id: response.name, text: value });
        })
        .catch((e) => console.log(e));
    },
    deleteToDo(value) {
      axios
        .delete(
          "https://todos-70068-default-rtdb.firebaseio.com/todos/" +
            value +
            ".json"
        )
        .then(() => {
          let index = this.todoList.findIndex((i) => {
            return i.id == value;
          });
          this.todoList.splice(index, 1);
        })
        .catch((e) => console.log(e));
    },
  },

  data() {
    return {
      todoList: [],
    };
  },
};
</script>
