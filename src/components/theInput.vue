<template>
  <div>
    <input @keypress.enter="addNewTask" type="text" placeholder="Your task" v-model="taskText">
    <button @click="addNewTask"><img src="../assets/plus.png" alt="plus"></button>
  </div>
</template>

<script>
export default {
  name: 'theInput',
  props: {
    //addFlag: {type: Boolean}
  },

  data() {
    return {
      taskText: '',
    }
  },

  methods: {
    complectedTask() {},

    deleteTask() {},

    editTask() {},

    addNewTask(){
      this.$emit('taskText', this.taskText, false)
      this.taskText = ''
    },

  },
}
</script>

<style scoped>

  input{
    padding: 15px;
    margin-left: 40px;
    width: 500px;
    background-color: rgba(255, 255, 255, 0.9);
    border-radius: 10px;
    border: none;
  }

  button{
    padding: 14px;
    margin: 15px;
    align-items: center;
    border-radius: 50px;
    background-color: rgba(255, 255, 255, 0.9);
    border: none;
  }

  img{
    height: 15px;
    width: 15px;
  }

</style>