<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    Click Me
  </div>
</template>

<script>
export default {

    props : ['delay'],
    data() {
      return {
        showBlock : false,
        timer : null,
        reactionTime : 0
      }
    },
    mounted(){
      console.log("Hello World");
      setTimeout(() => {
        this.showBlock = true; 
        this.startTimer()
      }, this.delay);
    },
    updated() {
      console.log("Updated");
    },
    unmounted() {
      console.log("Unmounted");
    },
    methods : {
      startTimer(){
        this.timer = setInterval(() => {
          this.reactionTime += 10;
        }, 10)
      },
      stopTimer(){
        clearInterval(this.timer);
        this.$emit('stop', this.reactionTime);
      },

    }
}
</script>

<style>
.block{
    padding: 100px 0;
    width: 400px;
    background-color: #0faf87;
    color : black;
    border-radius: 20px;
    margin: 40px auto;
    text-align: center;

}
</style>