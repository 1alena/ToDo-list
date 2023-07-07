<template>
  <div class="list">
    <ul id="list">
      <li v-for="task in tasks" :key="task.message" >
        <div>
          <input type="checkbox" id="checkbox">
          <label for="checkbox">{{ task.message }}</label>
        </div>
        <div>
          <button v-on:click="editTask">
            <img src="../assets/edit.png" alt="edit">
          </button>
          <button v-on:click="deleteTask">
            <img src="../assets/cross.png" alt="delete">
          </button>
        </div>
      </li>
    </ul>
    <theFooter />
  </div>
</template>

<script>
import theFooter from "@/components/theFooter.vue";

export default {
  name: 'ListWithTasks',
  components: {theFooter},
  props: {},

  data() {
    return {
      tasks: [
        {message: 'Go for a walk'},
        {message: 'Buy flowers for my mom'},
        {message: 'Buy cheese'},
        {message: 'Pick up documents'},
        {message: 'Wash the dishes'}
      ]
    }
  },

  methods: {
    complectedTask() {},

    deleteTask() {},

    editTask() {}
  },
}
</script>

<style scoped>
  .list {
    text-align: left;
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

  input{
    margin: auto 5px ;
    border-radius: 50px;
  }

  input:checked{
    color: rgba(105, 120, 184);
    border-color: rgba(105, 120, 184);
  }

</style>