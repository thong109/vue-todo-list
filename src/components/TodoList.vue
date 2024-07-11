<template>
  <div class="todo-list">
    <h2>Danh sách công việc</h2>
    <input type="text" v-model="newTodo" placeholder="Thêm mới công việc" />
    <button @click="addTodo">Thêm</button>
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        <div class="item">
          <input
            type="checkbox"
            v-model="todo.done"
            :class="{ 'todo-item': true, done: todo.done }"
          />
          <span :class="{ 'todo-strikethrough': todo.done }">{{ todo.text }}</span>
        </div>
        <button @click="removeTodo(index)">Xóa</button>
      </li>
    </ul>
  </div>
  <button @click="removeAllTodos">Xoá tất cả</button>

</template>

<script>
export default {
  data() {
    return {
      todos: [],
      newTodo: "",
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim()) {
        this.todos.push({ text: this.newTodo, done: false });
        this.newTodo = "";
      }
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    },
    removeAllTodos() {
      this.todos = [];
    },
  },
};
</script>

<style scoped>
.todo-list {
  font-family: sans-serif;
}

.item {
  width: 300px;
  flex: 0 0 auto;
  display: flex;
  justify-content: flex-start;
}

.todo-list ul {
  list-style: none;
  padding: 0;
}

.todo-list li {
  margin-bottom: 10px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: rgba(0,0,0,.16);
}

.todo-list input[type="checkbox"] {
  margin-right: 10px;
}

.todo-list button {
  cursor: pointer;
  border: none;
  padding: 5px 10px;
  background-color: #eee;
  border-radius: 5px;
  width: 100px;
  min-height: 56px;
}

input[type="text"] {
  width: 300px;
  height: 50px;
}

.todo-strikethrough {
  text-decoration: line-through;
}

.hidden {
  display: none;
}
</style>
