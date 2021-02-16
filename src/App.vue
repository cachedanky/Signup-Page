<template>
  <Signup />
</template>

<script>

import Signup from './components/SignupForm'

export default {
  name: 'App',
  components: {
    Signup
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
body{
 background-color: #000000;
background-image: linear-gradient(147deg, #000000 0%, #434343 74%);
  margin:0;
}
</style>
