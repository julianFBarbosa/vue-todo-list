<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import TodoList from "./components/TodoList.vue";
</script>

<template>
  <TodoList />
</template>

<style lang="scss">
@import "./styles/variables";

:root {
  font-size: 16px;
}

* {
  margin: 0;
  padding: 0;

  &:after,
  &:before {
    margin: 0;
    padding: 0;
  }
}

body {
  margin: 0;
  padding: 0;
  min-height: 100vh;
  background-color: $blue-1000;
}

#app {
  font-family: Helvetica, sans-serif;
  text-align: center;
  color: $blue-900;
  max-width: 468px;
  margin: 60px auto 0;
  background: $blue-100;
  box-shadow: 2px 2px 4px $blue-800, 3px 3px 6px $blue-900;
  padding: 24px 16px;
  border-radius: 8px;
}
</style>
