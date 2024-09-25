<template>
    <div class="max-w-lg mx-auto p-4">
      <h1 class="text-3xl font-bold mb-4">TO DO List</h1>
      <input 
        v-model="newTask" 
        type="text" 
        placeholder="Enter a task" 
        class="border p-2 w-full mb-4"
      />
      <button 
        @click="addTask" 
        class="bg-blue-500 text-white px-4 py-2 rounded-md"
      >
        Add Task
      </button>
      
      <div v-for="task in tasks" :key="task.id" class="mt-4">
        <TodoItem 
          :title="task.title" 
          :description="task.description"
          :id="task.id"
          @deleteTask="deleteTask"
        />
      </div>
    </div>
  </template>
  
  <script>
  import TodoItem from './Item.vue';
  
  export default {
    components: {
      TodoItem,
    },
    data() {
      return {
        newTask: '',
        tasks: [
          { id: 1, title: 'Task-1', description: 'Learn Backend' },
          { id: 2, title: 'Task-2', description: 'learn Frontend' },
        ],
      };
    },
    methods: {
      addTask() {
        if (this.newTask.trim()) {
          this.tasks.push({
            id: Date.now(),
            title: this.newTask,
            description: `Description for ${this.newTask}`,
          });
          this.newTask = '';
        }
      },
      deleteTask(id) {
        this.tasks = this.tasks.filter(task => task.id !== id);
      }
    },
  };
  </script>
  
  <style scoped>

  </style>
  