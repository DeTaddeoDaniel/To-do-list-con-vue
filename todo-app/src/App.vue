<template>
  <div class="container">
      <h1 class="text-center mt-3">To do list</h1>
      <todo-app/>
  </div>


</template>

  <script>
  import TodoApp from './components/todoApp.vue'

  export default {
  components: {TodoApp },
    name: 'App'
  }
  </script>

  <style>

  body{
    background-color: peru;
  }



  </style>
