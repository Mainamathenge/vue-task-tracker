<template>
 <div class = "container">

      <Header />
      <AddTask @add-task="AddTask"/>
      <Tasks @toggle-reminder="toggle-reminder" @delete-task="deleteTask" :tasks="tasks"/>
 </div>
</template>

<script>
import Header from './components/Header'
import Tasks from './components/Tasks'
import AddTask from './components/Addtask'
export default {
  name: 'App',
  components: {
   Header ,
   Tasks,
   AddTask
  },
  data(){
    return {
      task : []
    }
  },
  methods:{
    addTask(task){
      // eslint-disable-next-line no-undef
      this.tasks = [...this.tasks,task]
    },
    deleteTask(id){
      if (confirm('Are you Sure')){
      this.tasks = this.tasks.filter((task) => task.id !==id );
      console.log('task',id);
    }
  },
    toggleReminder(id){
      this.task = this.tasks.map((task) => 
      task.id ===id ? {
        ...task,reminder : !task.reminder } :task
      )
    },
    async fetchTasks(){
        const res = await fetch('http://localhost:5000/tasks');
        const data = res.json();
        return data;
    }
  },
  async created(){
    this.tasks = await this.fetchTasks();
    
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Poppins', sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}

</style>
