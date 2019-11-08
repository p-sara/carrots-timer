<template>
  <div id="app">
    <Timer msg="Welcome to Your Vue.js App"/>
    <div class="carrots-holder">
     <!-- <div class="carrot2"></div>-->
      <img v-for="i in 4"
           :key="i"
           alt="Carrot icon"
           class="carrot-icon1"
           :style="{ position: 'relative', top: `${Math.random() * Math.random() *  i * 950}px`, left:
           `${Math.random() * i * 750}px` }"
           src="./assets/carrot.png">
      <img v-for="i in 4"
           :key="i + 'lol'"
           alt="Carrot icon"
           class="carrot-icon2"
           :style="{ position: 'relative', top: `${Math.random() * Math.random() * i * 950}px`, right: `${Math.random()
            * i * 750}px` }"
           src="./assets/carrot.png">
    </div>
    <div>Icons made by <a href="https://www.flaticon.com/authors/wanicon" title="wanicon">wanicon</a> from <a href="https://www.flaticon.com/"                 title="Flaticon">www.flaticon.com</a> is licensed by <a href="http://creativecommons.org/licenses/by/3.0/"                 title="Creative Commons BY 3.0" target="_blank">CC 3.0 BY</a></div>
  </div>
</template>

<script>
import Timer from './components/Timer.vue'

export default {
  name: 'app',
  components: {
    Timer
  }
}
</script>

<style lang="scss">
html {
  height: 100%;
}
body {
  background-color: #db2f64;
  background-image: linear-gradient(to bottom right, #db2f64, #de8a69);
  background-repeat: no-repeat;
  overflow: hidden;
}

::selection {
    background: white; /* WebKit/Blink Browsers */
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
}

.carrots-holder {
  height: 100vh;
  width: 100vw;
  z-index: -100;
  opacity: 0.5;
  //background-image: url('./assets/carrot.png');
}

.carrot-icon1 {
  animation: turn1 30s linear infinite;
}

.carrot-icon2 {
  animation: turn2 30s linear infinite;
}

/*@keyframes move1 {
  0% {
    transform: translate(0px)
  }

  20% {
    transform: translate(-5px, 5px) rotate(15deg)
  }

  40% {
    transform: translate(5px, 5px)
  }

  60% {
     transform: translate(5px, -5px) rotate(-15deg)
   }

  80% {
    transform: translate(-5px, -5px) rotate(10deg)
  }

  100% {
    transform: translate(0px)
  }
}

@keyframes move2 {
  0% {
    transform: scaleX(-1) translate(0px)
  }

  20% {
    transform: scaleX(-1) translate(5px, -5px) rotate(-15deg)
  }

  40% {
    transform: scaleX(-1) translate(-5px, -5px)
  }

  60% {
    transform: scaleX(-1) translate(-5px, 5px) rotate(15deg)
  }

  80% {
    transform: scaleX(-1) translate(5px, 5px) rotate(-10deg)
  }

  100% {
    transform: scaleX(-1) translate(0px)
  }
}*/

@keyframes turn1 {
    0% {
        transform: translateY(-150vh) rotate(360deg)
    }

    100% {
        transform: translateY(150vh) rotate(0deg)
    }
}

@keyframes turn2 {
    0% {
        transform: translateY(-150vh) rotate(0deg)
    }

    100% {
        transform: translateY(150vh) rotate(360deg)
    }
}

/*@keyframes drop1 {
    0% {
        transform: translate(0)
    }

    100% {
        transform: translate(100vh)
    }
}*/
</style>
