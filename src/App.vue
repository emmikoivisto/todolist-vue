<template>
  <div id="app">

    <h1>{{title}}</h1>
    <form v-on:submit.prevent="saveNewTodo">
      <label for="todo-input">Add a ToDo:</label>
      <input type="text" id="todo-input" v-model="newTodo.name" />
      <label for="high">High</label>
      <input type="radio" id="high" v-model="newTodo.priority" value="high">
      <label for="low">Low</label>
      <input type="radio" id="low" v-model="newTodo.priority" value="low">
      <input type="submit" value="Save Item"/>
    </form>
    <ul>
      <li v-for="(todo, index) in todos" :key="index" :class="todo.priority" >
       <span>{{ todo.name }}</span>
      </li>
    </ul>


  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return {
      title: "ToDo's",
      todos: [
        {name: "Buy shopping", priority: "high"},
        {name: "Clean bathroom", priority: "low"},
        {name: "Car's MOT", priority: "high"}
      ],
      newTodo: {
        name: "",
        priority: null
      },
    }
  },
    methods: {
      saveNewTodo: function(){
        this.todos.push(this.newTodo);
        this.newTodo = {
          name: "",
          priority: null
        };
      },
    }
}
</script>

<style>
#app {
  width: 60%;
  margin: 0 auto;
  font-family: 'Lato', sans-serif;
}

ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

li {
  margin: 20px 0;
  padding: 10px;
  display: flex;
  justify-content: space-between;
}


li.high {
  border: 2px solid #f2360c;
  color: #f2360c;
}

li.low {
  border: 2px solid #1a681e;
}

input[type="text"] {
  padding: 10px;
  width: 50%;
  margin: 10px;
}

button{
  padding: 10px;
  background: #000;
  color: #fff;
  cursor: pointer;
  border: 1px solid #000;
}

</style>
