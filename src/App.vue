<script>
let id = 1;

export default {
  data() {
    return {
      newTodo: "",
      todos: [
        {
          id: id++,
          todoContext: "New task",
          isComplete: false,
        }
      ],
    }
  },
  methods: {
    addTodo() {
      if(this.newTodo) {
        this.todos.push(
          {
            id: id++,
            todoContext: this.newTodo,
            isComplete: false,
          }
        );
        this.newTodo = "";
      } else {
        alert("タスクを登録してください");
      }
    },
    removeTodo() {
      this.todos = this.todos.filter(todo => !todo.isComplete);
    }
  },
}
</script>

<template>
  <h1>My ToDo App</h1>
  <input type="text" v-model="newTodo"/>
  <button @click="addTodo">追加</button>
  <button @click="removeTodo">完了済みを削除する</button>
  <ul>
    <div v-if="todos.length > 0">
      <li v-for="(todo) in todos">
        <input type="checkbox" v-model="todo.isComplete"/>
        <span v-if="todo.isComplete" class="todo-done">
          {{ todo.todoContext }}
        </span>
        <span v-else> 
          {{ todo.todoContext }}
        </span>
      </li>
    </div>
    <div v-else>
      <p>"ToDoがまだありません！"</p>
    </div>
  </ul>
</template>

<style>
body {
  background-color: #eee;
}

.todo-done {
  text-decoration: line-through;
}
</style>