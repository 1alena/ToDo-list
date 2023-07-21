<template>
  <div class="list">
    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        <div>
          <input type="checkbox" id="checkbox" v-model="task.checkboxStatus">
          <label for="checkbox" v-if="task.editFlag===false" :class="{ completedTask: task.checkboxStatus }">{{ task.message }}</label>
          <input type="text" class="input" v-else v-model="task.message" @keypress.enter="task.editFlag = false">
        </div>
        <!--<input v-else @keypress.enter="task.addFlag = false" type="text" placeholder="Your task" v-model="task.message">-->
        <div>
          <button v-on:click="task.editFlag = true" v-if="task.editFlag===false">
            <img src="../assets/edit2.png" alt="edit" >
          </button>
          <button v-on:click="task.editFlag = false" v-if="task.editFlag===true">
            <img src="../assets/tick.png" alt="tick" >
          </button>
          <button v-on:click="deleteTask">
            <img src="../assets/cross.png" alt="delete">
          </button>
        </div>
      </li>
    </ul>
    <div v-show="!addFlag">
      <theInput @taskText="taskText" @keypress.enter="taskText" class="input"/>
    </div>
    <theFooter :taskCounter="taskCounter" @addNewFolder="addNewFolder"/>
  </div>
</template>

<script>
import theFooter from "@/components/theFooter.vue";
import theInput from "@/components/theInput.vue";

export default {
  name: 'ListWithTasks',
  components: {
    theFooter,
    theInput
  },
  props: {},

  data() {
    return {
      tasks: [
        {message: 'Go for a walk', editFlag: false, checkboxStatus: false},
        {message: 'Buy flowers for my mom', editFlag: false, checkboxStatus: false},
        {message: 'Buy cheese', editFlag: false, checkboxStatus: false},
        {message: 'Pick up documents', editFlag: false, checkboxStatus: false},
        {message: 'Wash the dishes', editFlag: false, checkboxStatus: false}
      ],

      addFlag: true,
    }
  },

  computed: {
    taskCounter() {
      return this.tasks.length
    }
  },

  methods: {
    completedTask(){

    },

    deleteTask() {
      this.tasks.splice(-1, 1)
      console.log(this.tasks.length)
      this.taskCounter--
    },

    editTask() {
      this.task.editFlag = false
    },

    addNewFolder(){
      this.addFlag = false
    },

    taskText(taskText){
      this.tasks.push({message: taskText, editFlag: false, checkboxStatus: false})
      this.addFlag = true
      this.taskCounter++
    }

  },
}
</script>

<style scoped>
  .list {
    text-align: left;
    margin-left: 0;
  }

  ul{
    max-height: 360px;
    overflow-y: scroll;
  }

  ::-webkit-scrollbar {
    width: 20px;/* ширина всей полосы прокрутки */
  }

  ::-webkit-scrollbar-track {
    border-radius: 15px;
    background: rgba(255, 255, 255, 0.9);/* цвет зоны отслеживания */
  }

  ::-webkit-scrollbar-thumb {
    //background-color: rgba(176, 196, 222);
    background-color: rgba(176, 224, 230);/* цвет бегунка */
    border-radius: 15px;/* округлось бегунка */
    border: 2px solid rgba(255, 255, 255, 0.9);/* отступ вокруг бегунка */
  }

  li {
    list-style: none;
    padding: 15px;
    margin: 10px 60px 10px 20px;
    background-color: rgba(255, 255, 255, 0.9);
    border-radius: 10px;

    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  li:hover{
    background-color: rgba(211, 217, 242, 0.9);
  }

  button{
    border: none;
    background: none;
    margin: auto 0 auto 10px;
  }

  img{
    height: 15px;
    width: 15px;
  }

  input{
    border-radius: 50px;
  }

  input:checked{
    color: rgba(105, 120, 184);
    border-color: rgba(105, 120, 184);
  }

  .input{
    border: white;
    border-radius: 15px;
  }

  .input:focus-visible{
    border: none;
  }

  .completedTask{
    color: gray;


  }

</style>