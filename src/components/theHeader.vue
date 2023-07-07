<template>
  <div class="header">
    <a v-on:click="toBack">
      <img src="../assets/toBack.png" alt="to back" >
    </a>
    <h1>{{ msg }}</h1>
    <a v-on:click="toForward">
      <img src="../assets/toForward.png" alt="to forward">
    </a>
  </div>
</template>

<script>
export default {
  name: 'theHeader',
  props: {
  },

  data() {
    return {
      msg: 'Monday'
    }
  },

  methods: {
    toBack(){},

    toForward() {}
  }
}
</script>

<style scoped>
  .header{
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  a{
    margin: 40px;
  }

  img{
    height: 30px;
    width: 30px;
  }
</style>