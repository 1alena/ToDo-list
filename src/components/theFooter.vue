<template>
  <div class="footer">
    <p>You have {{taskCounter}} tasks for this day!</p>
    <button v-on:click="addNewTask">
      <img src="../assets/plus.png" alt="plus">
      Add a new task
    </button>
  </div>
</template>

<script>
export default {
  name: 'theFooter',
  props: {
    tasksLength: {type: Number}
  },

  data() {
    return {
      taskCounter: this.tasksLength,
      taskText: ''
    }
  },

  methods: {
    addNewTask(){
      // taskText =
      this.taskCounter++

      this.$emit('taskText', this.taskText)
    },
  }
}
</script>

<style scoped>
  .footer{
    display: flex;
    justify-content: space-between;
    align-items: center;
    align-self: flex-end;
    margin-bottom: 0;
  }

  p{
    margin: 40px;
  }

  button{
    padding: 0 15px 0 0;
    margin: 40px;
    display: flex;
    align-items: center;
    text-align: center;
    border-radius: 50px;
    background-color: rgba(255, 255, 255, 0.9);
    border: none;
  }

  img{
    height: 25px;
    width: 25px;
    margin: 10px;
  }
</style>