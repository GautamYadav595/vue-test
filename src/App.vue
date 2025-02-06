<template>
  <div>
  <testComponet />
</div>
</template>

<script>

import testComponet from './components/testComponet.vue'

export default {
  name: 'App',
  components: {
   
    testComponet
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
  margin-top: 60px;
}
</style>
