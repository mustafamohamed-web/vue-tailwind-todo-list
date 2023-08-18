<template>
  <div class="grid grid-cols-4 grid-rows-6 gap-4 mx-5">
    <div
      v-for="task in filterPriority"
      :key="task.id"
      class="flex flex-col justify-center bg-slate-600 text-blacks border border-black rounded p-5 mt-5"
      :class="{ 'opacity-50': task.done }"
      :style="{ background: priorityBg(task.priority) }"
    >
      <div class="flex flex-col justify-between">
        <h1 class="font-bold capitalize" :class="{ 'line-through': task.done }">
          {{ task.name }}
        </h1>
        <p>{{ task.description }}</p>
        <p>{{ task.date }}</p>
        <p class="rounded text-black font-bold">
          {{ task.priority }}
        </p>
      </div>

      <div class="flex justify-center gap-3">
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
  <!-- <NoTasksModal :tasks="tasks" /> -->
</template>

<script setup>
import NoTasksModal from "./NoTasksModal.vue";
import { ref } from "vue";

const props = defineProps({
  filterPriority: Array,
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
const priorityBg = (priority) => {
  if (priority === "Low") {
    return "grey";
  } else if (priority === "Medium") {
    return "orange";
  } else {
    return "#A52A2A";
  }
};
console.log(props.tasks);
</script>
