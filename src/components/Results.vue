<template>
  <div id="results" :class="{ fast: time <= 300, normal: 300 < time && time < 1000, slow: 1000 <= time }">
    <h1>{{ time / 1000 }}s</h1>
    <h2>{{ message }}</h2>
  </div>
</template>

<script>
export default {
  name: "Results",
  props: ["time", "message"]
}
</script>

<style>
#results {
  width: 40em;
  height: 15em;
  border: 0.5rem solid #264653;
  border-radius: 20px;
}

h2 {
  font-size: 2em;
  margin: 0.5em 0;
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