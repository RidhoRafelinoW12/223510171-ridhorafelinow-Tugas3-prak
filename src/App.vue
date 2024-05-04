<template>
  <div id="app" class="container">
    <h1>Hal-hal yang menambah pahala!!</h1>
    <input type="text" v-model="newTodo" placeholder="Tambahake kegiatan koe" class="input-field" />
    <button @click="addTodo" class="add-button">Tambahkan Aktivitas Sampeyan</button>

    <ul class="todo-list">
      <li v-for="(todo, index) in todos" :key="index">
        {{ todo.text }}
        <button @click="editTodo(index, todo.text)" class="edit-button">Edit</button>
        <button @click="deleteTodo(index)" class="delete-button">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: "",
      todos: [],
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== "") {
        this.todos.push({ text: this.newTodo, originalText: this.newTodo });
        this.newTodo = "";
      }
    },
    deleteTodo(index) {
      this.todos.splice(index, 1);
    },
    editTodo(index, originalText) {
      const editedText = prompt("Enter new task");
      if (editedText) {
        this.todos[index].text = editedText;
      } else {
        this.todos[index].text = originalText;
      }
    },
  },
};
</script>

<style scoped>
.container {
  max-width: 600px;
  margin: 0 auto;
  background-color: rgba(255,255,255,0, 0.8); 
  background-image: url('pp1.JPEG');
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.input-field {
  width: 100%;
  height: 40px;
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
}

.add-button {
  width: 100%;
  height: 40px;
  background-color: #4CAF50;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.add-button:hover {
  background-color: #3e8e41;
}

.todo-list {
  list-style: none;
  padding: 50;
  margin: 0;
}

.todo-list li {
  padding: 10px;
  border-bottom: 1px solid #ccc;
  color: #fff; /* Tambahkan warna font putih */
  border: 1px solid #ccc;
}

.todo-list li:last-child {
  border-bottom: none;
}

.edit-button, .delete-button {
  width: 40px;
  height: 30px;
  background-color: #4CAF50;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.edit-button:hover, .delete-button:hover {
  background-color: #3e8e41;
}
</style>