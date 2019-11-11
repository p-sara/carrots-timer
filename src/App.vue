<template>
  <div id="app">
    <Timer/>
    <div class="carrots-holder">
      <img v-for="i in 8"
           :key="i"
           alt="Carrot icon"
           :class="`carrot-icon-${i}`"
           src="./assets/carrot.png">
      <!-- <img v-for="i in 4"
           :key="i + 'lol'"
           alt="Carrot icon"
           class="carrot-icon2"
           :style="{ position: 'relative', top: `${Math.random() * Math.random() * i * 950}px`, right: `${Math.random()
            * i * 750}px` }"
           src="./assets/carrot.png"> -->
    </div>
    <div class="icon-disclaimer">Icons made by <a href="https://www.flaticon.com/authors/wanicon" title="wanicon">wanicon</a> from <a href="https://www.flaticon.com/"                 title="Flaticon">www.flaticon.com</a> is licensed by <a href="http://creativecommons.org/licenses/by/3.0/"                 title="Creative Commons BY 3.0" target="_blank">CC 3.0 BY</a></div>
  </div>
</template>

<script>
import Timer from './components/Timer.vue'

export default {
  name: 'app',
  components: {
    Timer
  },
  computed: {
    carrotsAmount() {
      return Math.floor(Math.random() * 26 + 6) 
    }
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
  height: 100vh;
  width: 100vw;
}

.carrots-holder {
 
  z-index: -100;
  opacity: 0.7;
  isolation: isolate;
  //background-image: url('./assets/carrot.png');
}

.carrot-icon {
  @for $i from 1 through 8 {
     &-#{$i} {
       position: relative;
       //top: random(280 * $i) + px;
       right: random(500 * $i) + px;
      //animation shorthand( animation-name, duration, timing-function, delay, iteration-count)
       animation: turn1 10 + $i + s linear $i + s infinite;
    }
  }
  //animation: turn1 10s linear infinite;
}

.carrot-icon2 {
  animation: turn2 30s linear infinite;
}

.icon-disclaimer {
  font-size: 8px;
  position: relative;
  bottom: 1vh;
  a {
    color: #fff;
    text-decoration: none;
  }
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
