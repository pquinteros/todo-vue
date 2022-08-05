<template>
  <div id="app">
    <Todo :items=items />
    commit 1
    commit 2
  </div>
</template>

<script>

import Todo from './components/Todo.vue'

export default {
  name: 'App',
  data:function() {
return {
    items: [
      // { text: 'Leche' },
      // { text: 'Carne' },
      // { text: 'Huevos' }
    ]
  };
},
  components: {
    Todo
  }
}


</script>

<style>

@import url("https://fonts.googleapis.com/css2?family=Inter:wght@200;300;400;500;600;700;800&display=swap");

body{
  font-family: "Inter", sans-serif;
  background: #e4e9f3;
  display: flex;
  height: 100vh;
}

#app {
  /*font-family: Avenir, Helvetica, Arial, sans-serif;
  font-family: 'Inter', sans-serif;*/
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /*margin-top: 60px;*/
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  text-align: left;
}
</style>
