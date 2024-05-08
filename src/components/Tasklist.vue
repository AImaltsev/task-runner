<template>
  <h1>Task list</h1>
  <p>Please enter you task</p>
  <input type="text" v-model="newTask">
  <button @click="AddTask">add task</button>
  
  <div>
  <ul>
    <li v-for="(task, index) in taskArray" :key="index">
      <span>{{ task }}</span>
      <button @click="editTask(index)">edit</button>
      <button @click="deleteTask(index)">Delete</button>
      <input type="text" v-if="index === editIndex" v-model="textEditTask">
      <button v-if="index === editIndex" @click="saveTask(index)">Save</button>
    </li>
  </ul>
  </div>
</template>
  
<script>
export default{
  data() {
    return {
      newTask: '', 
      taskArray: [],
      editIndex: -1,
      textEditTask: '',
    };
  },
  methods: {
    AddTask() {
      if (this.newTask.trim() !== '') {
        this.taskArray.push(this.newTask);
        this.newTask = ''
      }
    },
    editTask(index){
      this.editIndex = index
      this.textEditTask = this.taskArray[index]
    },
    deleteTask(index) {
      this.taskArray.splice(index,1)
    },
    saveTask(index) {
      if (this.textEditTask.trim() !== '') {
        this.taskArray[index] = this.textEditTask;
        this.editIndex = -1;
        this.textEditTask = ''; 
  }
    },
  }
}
</script>
  
<style scoped>
  
</style>
  