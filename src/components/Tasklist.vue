<template>
  <h1>Task list</h1>
  <p>Please enter you task</p>
  <input type="text" v-model="newTask">
  <button @click="AddTask">add task</button>
  <div>
  <ul>
    <li v-for="(task, index) in taskArray" :key="index">{{ task }} <button @click="deleteTask(index)">Delete</button></li>
  </ul>
  </div>
</template>
  
<script>
export default{
  data() {
    return {
      newTask: '', 
      taskArray: [],
    };
  },
  methods: {
    AddTask() {
      if (this.newTask.trim() !== '') {
        this.taskArray.push(this.newTask);
        this.newTask = ''
      }
    },
    deleteTask(index) {
      this.taskArray.splice(index,1)
    },
  }
}
</script>
  
<style scoped>
  
</style>
  