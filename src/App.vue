<template>
  <div id="app">
    <message>Hey 👋🏼, check out my calculator done with vue</message>
    <card></card>
  </div>
</template>

<script>

import Message from './components/Message.vue';
import card from './components/card.vue';


export default {
  name: 'App',
  components: {
    Message,
    card
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding: 30px 10px;
}
</style>
