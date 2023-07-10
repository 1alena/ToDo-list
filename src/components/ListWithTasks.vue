<template>
  <div class="list">
    <ul id="list">
      <li v-for="(task, index) in tasks" :key="index">
        <div>
          <input type="checkbox" id="checkbox">
          <label for="checkbox">{{ task.message }}</label>
        </div>
        <!--<input v-else @keypress.enter="task.addFlag = false" type="text" placeholder="Your task" v-model="task.message">-->
        <div>
          <button v-on:click="editTask">
            <img src="../assets/edit.png" alt="edit" >
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
    <theFooter :tasksLength = 'tasks.length' @addNewFolder="addNewFolder"/>
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
        {message: 'Go for a walk'},
        {message: 'Buy flowers for my mom'},
        {message: 'Buy cheese'},
        {message: 'Pick up documents'},
        {message: 'Wash the dishes'}
      ],

      addFlag: true
    }
  },

  methods: {
    complectedTask() {},

    deleteTask() {},

    editTask() {},

    addNewFolder(){
      this.addFlag = false

    },

    taskText(taskText){
      this.tasks.push({message: taskText})
      this.addFlag = true
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
    width: 30px;/* ширина всей полосы прокрутки */
  }

  ::-webkit-scrollbar-track {
    background: orange;/* цвет зоны отслеживания */
  }

  ::-webkit-scrollbar-thumb {
    background-color: blue;/* цвет бегунка */
    border-radius: 20px;/* округлось бегунка */
    border: 3px solid orange;/* отступ вокруг бегунка */
  }

  li {
    list-style: none;
    padding: 15px;
    margin: 10px 40px 10px 0;
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

  input:checked{
    color: rgba(105, 120, 184);
    border-color: rgba(105, 120, 184);
  }

</style>