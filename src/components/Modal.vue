<template>
  <div class="max-w-md mx-auto bg-white p-8 rounded-md shadow-md">
    <h2 class="text-xl font-semibold mb-4">Add a New Task</h2>
    <form>
      <div class="mb-4">
        <label for="taskName" class="block font-medium">Task Name</label>
        <input
          type="text"
          id="taskName"
          name="taskName"
          class="w-full border rounded-md px-3 py-2 mt-1 focus:outline-none focus:ring focus:border-blue-300"
        />
      </div>
      <div class="mb-4">
        <label for="dueDate" class="block font-medium">Due Date</label>
        <input
          type="date"
          id="dueDate"
          name="dueDate"
          class="w-full border rounded-md px-3 py-2 mt-1 focus:outline-none focus:ring focus:border-blue-300"
        />
      </div>
      <div class="mb-4">
        <label for="description" class="block font-medium">Description</label>
        <textarea
          id="description"
          name="description"
          rows="3"
          class="w-full border rounded-md px-3 py-2 mt-1 focus:outline-none focus:ring focus:border-blue-300"
        ></textarea>
      </div>
      <button
        type="submit"
        class="w-full bg-blue-500 text-white rounded-md px-4 py-2 hover:bg-blue-600"
      >
        Add Task
      </button>
    </form>
  </div>
</template>

<script setup></script>
