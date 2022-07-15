<template>
<h4>Today Tasks</h4>  
<div class="tasks">
<div 
      class="task"
      :class="{ completed: task.isCompleted }"
      v-for="task in tasks"
      :key="task._id"
      @click="completedHandler(task._id)"
   >

  <div 
        class="round"
        :class="{ 
        business: task.type === 'business', 
        personal: task.type === 'personal',
        }"
        
        ></div>

    <span>{{task.name}}</span>
  </div>
</div>
  <div class="add-task">
    <input type="text" placeholder="Название задачи" v-model="taskName" />
    <button @click="addTask">+</button>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  data(){
    return {
      taskName: "",
      tasks: [{
        _id: "wadawdawdwa",
        name: "Create to do app in Vue js",
        isCompleted: false,
        type: "personal",
      }
      ]
    }
  },
    methods:{
      completedHandler:function(taskid){
        const currentTask=this.tasks.find((t)=> t._id==taskid);
        currentTask.isCompleted = !currentTask.isCompleted;
    },

    addTask: function(){
      this.tasks.push({
        _id: Math.random().toString(36).substring(2, 7),
        name: this.taskName,
        isCompleted: false,
        type: "personal",
       });
    },
  },
};
</script>
