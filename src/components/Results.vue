<template>
  <div id="results" :class="{ fast: time <= 300, normal: 300 < time && time < 1000, slow: 1000 <= time }">
    <h2>Your time</h2>
    <h1>{{ time / 1000 }}s</h1>
    <h2 v-if="time <= 300">Extreme</h2>
    <h2 v-if="300 < time && time < 1000">Just okay</h2>
    <h2 v-if="1000 <= time">Turtle</h2>
  </div>
</template>

<script>
export default {
  name: "Results",
  props: ["time"]
}
</script>

<style>
#results {
  width: 48em;
  height: 28em;
  border: 0.5rem solid #264653;
  border-radius: 20px;
}

h2 {
  font-size: 2em;
  margin: 1.5em 0;
}

.fast {
  background-color: #ffd166;
}

.normal {
  background-color: #e5e5e5;
}

.slow {
  background-color: #f94144;
}
</style>