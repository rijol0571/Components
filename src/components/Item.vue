<template>
    <div class="bg-gray-100 p-4 rounded-lg flex justify-between items-center">
      <div>
        <h2 class="font-semibold text-xl">{{ title }}</h2>
        <p class="text-gray-600">{{ description }}</p>
      </div>
      <div>
        <button class="bg-purple-500 text-white px-3 py-1 rounded-md mr-2">Edit</button>
        <button 
          @click="$emit('deleteTask', id)" 
          class="bg-red-500 text-white px-3 py-1 rounded-md"
        >
          Delete
        </button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      title: String,
      description: String,
      id: Number
    },
    created() {
      console.log(`Task with ID: ${this.id} was created.`);
    },
    mounted() {
      console.log(`Task with title: ${this.title} was mounted.`);
    }
  };
  </script>
  
  <style scoped>
  /* Tailwind classes handle styling */
  </style>
  