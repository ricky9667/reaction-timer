<template>
  <img id="logo" alt="Timer Logo" src="./assets/clock.png" >
  <h1>Reaction Timer</h1>
  <button class="button">Play</button>

  <Block></Block>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    Block,
    Results
  }
}
</script>

<style>
html {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  background-color: #00f5d4;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#logo {
  height: 160px;
  width: auto;
}

.button {
  padding: 16px 48px;
  margin-bottom: 24px;
  font-size: large;
  color: #ade8f4;
  background-color: #264653;
  border-radius: 8px;
  border: 2px solid #ade8f4;
  transition: 0.2s;
}

.button:hover {
  color: #264653;
  background-color: #ade8f4;
  border: 2px solid #264653;
}
</style>
