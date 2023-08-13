<template>
  <div class="grid grid-cols-4 grid-rows-6 gap-4 mx-5">
    <div
      v-for="(task, index) in tasks"
      :key="index"
      class="flex items-center justify-between text-white border border-black rounded p-5 mt-5"
      :style="{ backgroundColor: task.color }"
      :class="{ 'opacity-50': task.done }"
    >
      <h1 :class="{ 'line-through': task.done }">{{ task.name }}</h1>
      <input type="checkbox" v-model="task.done" class="mr-2" />
    </div>
  </div>
  <NoTasksModal />
</template>

<script setup>
import NoTasksModal from "./NoTasksModal.vue";
const props = defineProps({
  tasks: Array,
});
</script>
