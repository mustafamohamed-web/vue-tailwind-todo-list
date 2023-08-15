<template>
  <div class="grid grid-cols-4 grid-rows-6 gap-4 mx-5">
    <div
      v-for="task in items"
      :key="task.id"
      class="flex items-center justify-between text-white border border-black rounded p-5 mt-5"
      :style="{ backgroundColor: task.color }"
      :class="{ 'opacity-50': task.done }"
    >
      <h1 :class="{ 'line-through': task.done }">{{ task.name }}</h1>
      <div class="flex">
        <input type="checkbox" v-model="task.done" class="mr-2" />
        <img
          src="../icons8-delete-button.svg"
          @click="deleteTask(task.id)"
          class="cursor-pointer"
          alt=""
        />
      </div>
    </div>
  </div>
  <NoTasksModal :tasks="tasks" />
</template>

<script setup>
import NoTasksModal from "./NoTasksModal.vue";
import { ref } from "vue";

const props = defineProps({
  tasks: Array,
  getRandomColour: Function,
});

const items = ref(props.tasks);
console.log("Initial items.value:", items.value);

const deleteTask = (id) => {
  console.log("Deleting task with ID:", id);
  if (items.value.length > 0) {
    items.value = items.value.filter((task) => {
      return task.id !== id;
    });
    console.log("After deletion, items.value:", items.value);
  } else {
    console.log("no tasks");
  }
};
</script>
