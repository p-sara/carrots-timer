<template>
  <div class="timer">
    <h1>{{ msg }}</h1>
      <div v-if="inputVisible">
          <input type="number"
                 min="0"
                 placeholder="Liczba minut"
                 v-model="startValue">
          <button :disabled="startValue === null"
                  @click="setTimer()">Start</button>
      </div>
      <div v-else>
          <h3>{{timer.minutes}}:{{timer.seconds < 10 ? '0' + timer.seconds : timer.seconds}}
          </h3>
          <button @click="resetTimer()">Reset</button>
      </div>
  </div>
</template>

<script>
export default {
  name: 'Timer',
  props: {
    msg: String
  },
  data: () => ({
    startValue: null,
    inputVisible: true,
    timer: {
        minutes: null,
        seconds: null
    }
  }),
  methods: {
    setTimer() {
      this.inputVisible = false;
      this.countdown(this.startValue);
    },
    countdown(timerValue) {
      let initialMinutes = timerValue;
      let initialSeconds = 60;
      this.timer.minutes = parseInt(initialMinutes / 60, 10);
      this.timer.seconds = parseInt(initialSeconds % 60, 10);
      // let date = new Date;
//      console.log(date.getMinutes())
//      console.log(date.getSeconds())
        const countFunction = setInterval(() => {
            //this.timer.minutes = initialMinutes-=1;
            this.timer.seconds = initialSeconds < 0 ? 60 : initialSeconds-=1;


            console.log()
                //this.timerValue = initial-=1;
                if (initialMinutes <= 0 || this.startValue === null) {
                  clearInterval(countFunction)
                }
            }, 1000)
        // https://stackoverflow.com/questions/20618355/the-simplest-possible-javascript-countdown-timer
    },
    resetTimer() {
      this.inputVisible = true;
      this.startValue = null;
    }
  }
}
</script>

<style scoped>
.timer {
    background: #db2f64;
    color: white;
    width: 50%;
    height: 200px;
    position: absolute;
    left: 25%;
    top:25%;
    z-index: 10000;

}
</style>
