<template>
  <div class="flex flex-col items-center mt-5">
    <div class="flex w-full justify-center">
      <input
        v-model="selectedPriority"
        class="border w-1/4 border-black rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"
      />
      <img
        src="../icons8-plus.svg"
        @click="toggleModal"
        class="cursor-pointer h-10 w-10 bg-white"
        alt=""
      />
    </div>
  </div>
  <Modal :tasks="tasks" />
  <Tasks :filterPriority="filterPriority" />
</template>

<script setup>
import { ref, watch, computed } from "vue";
import Tasks from "./Tasks.vue";
import Modal from "./Modal.vue";

const tasks = ref([]);
const isModal = ref(false);
const selectedPriority = ref("");

console.log("selectedPriority:", selectedPriority.value);

const filterPriority = computed(() => {
  if (selectedPriority.value === "") {
    return tasks.value;
  } else {
    console.log;
    const filter = tasks.value.filter(
      (item) => item.priority === selectedPriority.value
    );
    return filter;
  }
});
console.log("filterPriority:", filterPriority.value);

const toggleModal = () => {
  isModal.value = !isModal.value;
  console.log("Modal toggled", isModal.value);
};

watch(
  () => tasks.value.length,

  (newLength) => {
    isModal.value = newLength === 0;
  }
);
</script>
