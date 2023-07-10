<template>
  <div class="footer">
    <p>{{ changeFinishText }}</p>
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
    taskCounter: {type: Number}
  },

  data() {
    return {
      addFlag: true
    }
  },

  computed:{
    changeFinishText() {
      if (this.taskCounter === 0){
        return `You have completed all the tasks!`
      } else {
        return `You have only ${this.taskCounter} tasks!`
      }
    },
  },

  methods: {

    addNewTask(){
      this.$emit('addNewFolder')
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