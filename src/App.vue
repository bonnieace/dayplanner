<template>
  <div id="app">
    <h1>To-Do List</h1>
    <form @submit.prevent="addTask">
      <input v-model="newTask" placeholder="Enter a task" />
      <button type="submit">Add Task</button>
    </form>
    <ul>
      <li 
        v-for="(task, index) in tasks" 
        :key="index" 
        :class="{ completed: task.completed }"
      >
        <input type="checkbox" v-model="task.completed" />
        {{ task.name }}
        <button @click="removeTask(index)">Remove</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: '',
      tasks: [],
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim()) {
        this.tasks.push({ name: this.newTask, completed: false });
        this.newTask = '';
      }
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 50px;
}

.completed {
  text-decoration: line-through;
  color: gray;
}
</style>
