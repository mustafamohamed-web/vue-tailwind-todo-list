<template>
  <div class="max-w-md mx-auto bg-white p-8 rounded-md shadow-md">
    <h2 class="text-xl font-semibold mb-4 text-green-950">Add a New Task</h2>
    <form>
      <div class="mb-4">
        <label for="taskName" class="block font-medium text-green-950"
          >Task Name</label
        >
        <input
          type="text"
          v-model="searchInput"
          name="taskName"
          class="w-full border rounded-md px-3 py-2 mt-1 focus:outline-none focus:ring focus:border-blue-300 text-green-950"
        />
      </div>

      <div class="mb-4">
        <label for="description" class="block font-medium text-green-950"
          >Description</label
        >
        <textarea
          v-model="description"
          name="description"
          rows="3"
          class="w-full border rounded-md px-3 py-2 mt-1 focus:outline-none focus:ring focus:border-blue-300text-green-950"
        ></textarea>
      </div>
      <div class="mb-4">
        <label for="dueDate" class="block font-medium">Due Date</label>
        <input
          type="date"
          v-model="date"
          name="dueDate"
          class="w-full border rounded-md px-3 py-2 mt-1 focus:outline-none focus:ring focus:border-blue-300 text-green-950"
        />
      </div>
      <div class="mb-4 flex justify-between">
        <div>
          <h1 class="font-medium">Priority</h1>
        </div>
        <select
          class="cursor-pointer border-2 rounded border-green-950"
          v-model="priority"
          id=""
        >
          <option value=""></option>
          <option value="Low">Low</option>
          <option value="Medium">Medium</option>
          <option value="High">High</option>
        </select>
      </div>

      <button
        type="submit"
        class="w-full bg-green-950 text-white rounded-md px-4 py-2 hover:bg-green-900"
        @click.prevent="addTask"
      >
        Add Task
      </button>
    </form>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { v4 as uuidv4 } from "uuid";
const date = ref("");
const description = ref("");
const priority = ref("");
const searchInput = ref("");

const props = defineProps({
  tasks: Array,
});

const addTask = () => {
  const newTask = {
    name: searchInput.value,
    done: false,
    id: uuidv4(),
    date: date.value,
    description: description.value,
    priority: priority.value,
  };

  props.tasks.push(newTask);
  searchInput.value = "";
};
</script>
