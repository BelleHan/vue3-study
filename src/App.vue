<template>
  <div class="container">
    <h4>count: {{ count }}</h4>
    <h4>double count coumputed: {{ doubleCountCoumputed }}</h4> 
    <h4>double count coumputed: {{ doubleCountCoumputed }}</h4> 
    <h4>double count method: {{ doubleCountMethod() }}</h4>
    <h4>double count method: {{ doubleCountMethod() }}</h4>
    <button @click="count++">Add One</button>
    <h2>To-Do List</h2>
    <TodoSimpleForm @add-todo="addTodo"/>
    
    <div v-if="!todos.length">
      추가된 Todo가 없습니다
    </div>
    <TodoList 
      :todos="todos" 
      @toggle-Todo="toggleTodo"
      @delete-todo="deleteTodo"
    />
  </div>

</template>

<script>
import { ref, computed } from 'vue';
import TodoSimpleForm from './components/TodoSimpleForm.vue'
import TodoList from './components/TodoList.vue';

export default {
  components: {
    TodoSimpleForm,
    TodoList,
  },
  setup() {
    const todos = ref([]);
    const todoStyle = {
      textDecoration: 'line-through',
      color: 'gray'
    }

    const addTodo = (todo) => {
      todos.value.push(todo);
    };

    const deleteTodo = (index) => {
      todos.value.splice(index, 1);
    };

    const toggleTodo = (index) => {
      console.log(todos.value[index]);
      todos.value[index].completed = !todos.value[index].completed;
      console.log(todos.value[index]);
    };

    const count = ref(1);
    const doubleCountCoumputed = computed(() => {
      console.log('computed');
      return count.value * 2;
    });

    const doubleCountMethod = () => {
      console.log('method');
      return count.value * 2;
    };
 
    return {
      todos,
      addTodo,
      todoStyle,
      deleteTodo,
      toggleTodo,
      count,
      doubleCountCoumputed,
      doubleCountMethod,
    };
  }
}
</script>

<style>
  .todo{
    color: gray;
    text-decoration: line-through;
  }
</style>