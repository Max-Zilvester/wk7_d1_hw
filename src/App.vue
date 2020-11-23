<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <h1>My First Vue Project</h1>

    <form v-on:submit.prevent="addNewTask">
      <label for="new-task">Add New Task:</label>
      <input id="new-task" type="text" v-model="newTask"/>

      <label class="radio-inline">High</label>
      <input id="rad1" type="radio" v-on:something="clicked" value="Rad1" name="optradio" v-model="picked" checked>
    
      <label class="radio-inline">Low</label>
      <input id="rad2" type="radio" v-on:something="clicked" value="Rad2" name="optradio" v-model="picked">
      <span>{{picked}}</span>

      <input class="but1" type="submit" value="Add new Task">
    </form>
    <ul>
      <li v-for="(task, index) in tasks" :key="index" :class="task.isCompleted ? 'completed':'not-completed'">
        <div id="con">
        <span>{{task.name}}</span>
        </div>
        <span v-if="task.isCompleted">Completed</span>
        <button class="but2" v-if="!task.isCompleted" v-on:click="doTask(index)">Complete</button>
      </li>
    </ul>
  </div>
  
</template>

<script>
export default {
  data(){
    return {
      tasks: [
        {name: "Buy shopping", isCompleted: true},
        {name: "Clean bathroom", isCompleted: false},
        {name: "Car's MOT", isCompleted: false},
        ],
      newTask: ""

    }
  },
  methods: {
    addNewTask: function(){
      this.tasks.push({
        name: this.newTask,
        isCompleted: false
      });
      this.newTask = "";
    },
    doTask: function(index){
      this.tasks[index].isCompleted = true;
    },
    clicked: function(){
      console.log(this.clicked)
    }
  }
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  width: 40%;
  text-align: center;
  color: #2c3e50;
  margin: 0 auto;
}

li {
  margin: 15px 0;
  padding: 10px;
  border-radius: 20px;
  display: flex;
  justify-content: space-between;
}

button {
  background-color: #4CAF50;
  border-radius: 8px;
}
button:hover {
  background-color: #b4c790;
}

.but1 {
  margin-left: 20px;
}

.but2 {
  margin-left: 60px;
}

#con {
  width: 100%;
}

li.completed {
  border: 2px solid #1a681e;
  box-sizing: border-box;
  color: #8b624a;
  widows: 50;
}

li.not-completed {
  border: 2px solid #f2360c;
}

rad1 {
  margin-left: 20px;
}


</style>
