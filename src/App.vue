<template>
  <div class="container">
    <img id="logo" alt="Timer Logo" src="./assets/clock.png" >
    <h1>Reaction Timer</h1>
    <button class="button {}" :disabled="isPlaying" @click="startGame">Start</button>
    <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
<!--    <p v-if="showResults">Reaction time: {{ score }}</p>-->
    <Results v-if="showResults" :time="score" :message="getMessageFromScore(score)"/>
<!--    <div v-if="mode === 'results'">-->
<!--      <Results :time=reactionTime />-->
<!--      <button class="button">Restart</button>-->
<!--    </div>-->
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
      isPlaying: false,
      delay: 0,
      score: 0,
      showResults: false,
      message: ["Fast", "Medium", "Slow"]
    };
  },
  methods: {
    startGame() {
      this.delay = 1000 + Math.random() * 2000
      this.isPlaying = true
      this.showResults = false
    },
    endGame(reactionTime) {
      this.isPlaying = false
      this.showResults = true
      this.score = reactionTime
    },
    getMessageFromScore() {
      let index = 1
      if (this.score < 300) index = 0
      if (this.score > 1000) index = 2
      return this.message[index]
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
  padding: 1rem 2.5rem;
  margin: 1.5em 0;
  font-size: 1.5rem;
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

.button:disabled {
  color: #111111;
  background-color: #666666;
  border: 0.2rem solid #ffffff;
}
</style>
