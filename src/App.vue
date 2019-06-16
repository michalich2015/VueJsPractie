<template>
  <div id="app">
    <div class="stats">
      <h3 class="stats__title">{{"Active tasks: "+tasks.length}} </h3>
      <Task :data="data" v-for="(data,index) in tasks" :key="index"  @delete-todo="deleteToDo"/>
    </div>
    <div class="add_task">
      <div class="add_task__input">
        <input type="text" v-model="new_task.title" placeholder="New Task">
        <textarea v-model="new_task.desc" placeholder="Description"></textarea>
      </div>
      <button class="add_task__btn" @click="add_task">➕</button>
    </div>
  </div>
</template>

<script>
import Task from './components/Task.vue'

export default {
  
  name: 'app',
  data(){
    return{
      new_task:{
        title:'',
        desc:''
      },
      tasks:[{
            title:"Ця программа гамно",
            desc:"Слава україні"
        },
        {
            title:'Путін',
            desc:'Брат порошенко'
        }
        ]
    }
  },
  components: {
    Task
    },
    methods:{
    deleteToDo(index){
      this.tasks.splice(index,1);
    },
    add_task(){
      if(this.new_task.title!='')
      {
          this.tasks.push({
            title:this.new_task.title,
            desc:this.new_task.desc
          });
          this.new_task.title='';
          this.new_task.desc='';
      }
    }
  } 
  }

</script>

<style>
:root {
  --main: #2F4858;
  --white: #fff;
}
* {
  padding: 0;
  margin: 0;
  transition: all 0.3s;
}
#app{
  width: 320px;
  box-shadow: 0 3px 20px #00000023;
  font-family: 'Gilroy', sans-serif;
  padding: 10px;
  margin: 20px 0 0 20px;
  color: var(--main);
}
.stats {
  margin: 0px;
}
.stats__title {
  margin: -10px -10px 10px -10px;
  padding: 10px;
  background-color: var(--main);
  color: var(--white);
  font-weight: 500;
}
.task {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  margin: -10px -10px 10px -10px;
  padding: 10px;
  max-width: 100%;
}
.task:hover {
  background-color: #2f485811;
}
.task__title {
  font-size: 18px;
}
.task__desc {
  font-weight: 500;
  font-size: 16px;
}
.task__done {
  height: 30px;
  width: 30px !important;
  border: none;
  background-color: unset;
}
.task__done:hover {
  cursor: pointer;
  border-radius: 4px;
  background-color: #9ee493bb;
}
.add_task {
  display: flex;
  
}
.add_task__input {
  width: 80%;
}
.add_task__input input, textarea {
  width: 100%;
  max-width: 100%;
  padding: 5px 0 5px 5px;
  font-family: 'Gilroy',sans-serif;
  border: 2px solid #2f485811;
  border-radius: 4px;
}
.add_task__input input {
  margin-bottom: 5px;
}
.add_task__btn {
  width: 20%;
  border: none;
  margin-left: 20px;
  background-color: unset;
}
.add_task__btn:hover {
  cursor: pointer;
  border-radius: 4px;
  background-color: #2f485811;
}

</style>
