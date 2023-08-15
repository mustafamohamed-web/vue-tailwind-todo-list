<template>
  <div class="flex flex-col items-center mt-5">
    <div class="flex w-full justify-center">
      <input
        type="text"
        class="border w-1/4 border-black rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"
        placeholder="Add Task"
        @click="showModal"
      />
      <img src="../icons8-plus.svg" class="cursor-pointer h-10 w-10" alt="" />
    </div>
  </div>
  <Modal v-if="btn" />
  <Tasks :tasks="tasks" :getRandomColour="randomColour" />
</template>

<script setup>
import { ref, computed } from "vue";
import Tasks from "./Tasks.vue";
import Modal from "./Modal.vue";
import { v4 as uuidv4 } from "uuid";
const searchInput = ref("");
const tasks = ref([]);

const isModal = ref(false);

const showModal = computed(() => {
  isModal.value = !isModal.value;
});

const addTask = computed(() => {
  const newTask = {
    name: searchInput.value,
    color: randomColour(),
    done: false,
    id: uuidv4(),
  };

  tasks.value.push(newTask);
  searchInput.value = "";
});

const randomColour = () => {
  const r = Math.floor(Math.random() * 256);
  const g = Math.floor(Math.random() * 256);
  const b = Math.floor(Math.random() * 256);
  return `rgb(${r},${g},${b})`;
};
</script>
