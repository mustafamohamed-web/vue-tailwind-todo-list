<template>
  <Header />
  <AddTask />
  <Tasks :tasks="tasks" />
</template>

<script setup>
import Header from "./components/Header.vue";
import Tasks from "./components/Tasks.vue";
import AddTask from "./components/AddTask.vue";
</script>
