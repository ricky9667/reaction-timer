<template>
  <div class="container">
    <img id="logo" alt="Timer Logo" src="./assets/clock.png" >
    <h1>Reaction Timer</h1>
    <button class="button" v-if="mode === 'initial'" @click="startGame">Start</button>
    <Block v-if="showBlock" @click="blockClicked" />
    <div v-if="mode === 'results'">
      <Results :time=reactionTime />
      <button class="button">Restart</button>
    </div>
  </div>
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
  },
  data() {
    return {
      mode: 'initial',
      showBlock: false,
      appearTime: 0,
      reactionTime: 0
    };
  },
  methods: {
    startGame() {
      this.mode = 'play'
      let interval = Math.random() * 3000

      setTimeout(() => {
        this.showBlock = true
        this.appearTime = Date.now()
      }, interval)
    },
    blockClicked() {
      this.reactionTime = Date.now() - this.appearTime
      this.showBlock = false
      this.mode = 'results'
      console.log(this.reactionTime)
    }
  }
}
</script>

<style>
html {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  background-color: #00f5d4;
}

.container {
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
  text-align: center;
}

.container h1 {
  font-size: 4rem;
  margin-bottom: 1.5em;
}


#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 4rem;
}

#logo {
  height: 20rem;
  width: auto;
}

.button {
  padding: 2rem 5rem;
  margin: 2em 0;
  font-size: 2.5rem;
  color: #ade8f4;
  background-color: #264653;
  border-radius: 8px;
  border: 0.2rem solid #ade8f4;
  transition: 0.2s;
}

.button:hover {
  color: #264653;
  background-color: #ade8f4;
  border: 0.2rem solid #264653;
}
</style>
