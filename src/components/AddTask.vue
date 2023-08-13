<template>
  <div class="flex flex-col items-center mt-5">
    <div class="flex w-full justify-center">
      <input
        type="text"
        class="border w-1/4 border-black rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"
        placeholder="Add Task"
        v-model="searchInput"
      />
      <button
        @click="addTask"
        class="border rounded-lg ml-2 p-2 border-black mt-5"
      >
        Add Task
      </button>
    </div>
    <div class="flex gap-2 w-full justify-center">
      <button
        @click="delTask"
        class="w-1/4 border rounded-lg p-2 border-black mt-5 hover:bg-red-500 hover:border-white hover:text-white"
      >
        Clear All
      </button>
      <button
        @click="deleteCheckedTasks"
        class="border w-1/4 rounded-lg p-2 border-red-500 mt-5 hover:bg-black hover:border-white hover:text-white"
      >
        Delete Checked
      </button>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";
const searchInput = ref("");
const tasks = ref([]);

const addTask = computed(() => {
  const newTask = {
    name: searchInput.value,
    color: randomColour(),
    done: false,
  };

  tasks.value.push(newTask);
  searchInput.value = "";
});

const delTask = () => {
  tasks.value = "";
  searchInput.value = "";
};

const randomColour = () => {
  const r = Math.floor(Math.random() * 256);
  const g = Math.floor(Math.random() * 256);
  const b = Math.floor(Math.random() * 256);
  return `rgb(${r},${g},${b})`;
};

const deleteCheckedTasks = () => {
  tasks.value = tasks.value.filter((task) => !task.done);
};
</script>
