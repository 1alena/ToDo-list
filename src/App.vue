<template>
  <div id="app">
    <div class="box">
      <theHeader msg="Monday"/>
      <ListWithTasks />
    </div>
  </div>
</template>

<script>
import theHeader from './components/theHeader.vue'
import ListWithTasks from './components/ListWithTasks.vue'

export default {
  name: 'App',
  components: {
    theHeader,
    ListWithTasks,
  }
}
</script>

<style>
  body{
    background: linear-gradient(to bottom right , #aea4e3, #d3ffe8);
  }

  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }

  .box {
    margin: 140px 300px;
    border: 5px black;
    background-color: rgba(255, 255, 255, 0.6);
    height: 700px;
    align-items: flex-end;
    box-shadow: 10px 10px 5px rgba(85, 105, 115);
    border-radius: 5px;
  }

</style>
