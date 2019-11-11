<template>
  <div class="timer">
    <h3>{{ msg }}</h3>
      <div v-if="inputVisible">
          <input type="number"
                 min="0"
                 placeholder="Liczba minut"
                 v-model="startValue"
                 @keyup.enter="setTimer(startValue)">
          <button :disabled="startValue === null"
                  @click="setTimer(startValue)">Start</button>
      </div>
      <div v-else>
          <h3>{{timer}}</h3>
          <button @click="resetTimer()">Reset</button>
      </div>
  </div>
</template>

<script>
export default {
  name: 'Timer',
  data: () => ({
    msg: 'Meet-up starts in',
    startValue: null,
    inputVisible: true, 
    timer: null
  }),
  methods: {
    setTimer(val) {
      this.inputVisible = false;
      this.countdown(val);
    },
    countdown(duration) {
      let timer = duration * 60, minutes, seconds;
      this.timer = `${duration}:00`;

      const lol = setInterval(() => {
          minutes = parseInt(timer / 60, 10);
          seconds = parseInt(timer % 60, 10); 

          seconds = seconds < 10 ? "0" + seconds : seconds;

          this.timer = `${minutes}:${seconds}`

          if (--timer < 0) {
            this.timer = "Yay! It's time to start"
            this.msg = ''
          } 

          if (!this.startValue) {
            clearInterval(lol)
          }
        }, 1000)
    },
    resetTimer() {
      this.inputVisible = true;
      this.startValue = null;
    }
  }
}
</script>

<style lang="scss" scoped>
.timer {
    //background: #db2f64;
    background: #ffffffc7;
    color: white;
    width: 50%;
    height: 200px;
    position: absolute;
    left: 25%;
    top:25%;
    z-index: 10000;
    mix-blend-mode: exclusion
}
</style>
