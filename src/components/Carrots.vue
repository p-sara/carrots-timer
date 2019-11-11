<template>
    <div class="carrots-holder">
      <img v-for="i in 80"
           :key="i"
           alt="Carrot icon"
           :style="{transform: `translate(${Math.random() * 10}px, ${Math.random() * 10}px)`}"
           :class="`carrot-icon-${i}`"
           src="./../assets/carrot.png">
    </div>
</template>

<script>

export default {
  name: 'Carrots',
  computed: {
    carrotsAmount() {
      return Math.floor(Math.random() * 26 + 6) 
    }
  }
}
</script>

<style lang="scss">

.carrots-holder {
 
  z-index: -100;
  opacity: 0.7;
  isolation: isolate;
  //background-image: url('./assets/carrot.png');
}

.carrot-icon {
  @for $i from 1 through 80 {
     &-#{$i} {
       position: relative;
       //top: random(280 * $i) + px;
       //right: random(10 * $i) + vh;
      //animation shorthand( animation-name, duration, timing-function, delay, iteration-count)
       animation: turn1 10 + $i + s linear 0s infinite;
    }
  }
  //animation: turn1 10s linear infinite;
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
</style>
