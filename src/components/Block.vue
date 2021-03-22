<template>
  <div id="block" v-if="showBlock" @click="stopTimer">
    <h3>Click Me</h3>
  </div>
</template>

<script>
export default {
  name: "Block",
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0
    }
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true
      this.startTimer()
    }, this.delay)
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10
      }, 10)
    },
    stopTimer() {
      clearInterval(this.timer)
      console.log(this.reactionTime)
      this.$emit("end", this.reactionTime)
    }
  }
}
</script>

<style>
#block {
  width: 40em;
  height: 15em;
  color: #e0fbfc;
  background-color: #3d5a80;
  border-radius: 20px;

  display: flex;
  justify-content: center;
  align-items: center;
}
</style>