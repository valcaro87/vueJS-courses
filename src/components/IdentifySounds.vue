<template>
  <div>
    <h2>what sound is this?</h2>
    <!-- <h3>{{ clicks }} / {{ score() }}</h3> -->

    <div>
      <div class="animals" @click="clickAnimal('dog')" :class="isError && animalClicked == 'dog' ? 'oohh' : ''">
        <img src="https://img.freepik.com/free-vector/one-cute-dog-white-background_1308-44313.jpg?w=2000" alt="">
      </div>
      <div class="animals" @click="clickAnimal('cat')" :class="isError && animalClicked == 'cat' ? 'oohh' : ''">
        <img
          src="https://img.freepik.com/premium-vector/cute-white-cat-cartoon-vector-illustration_42750-808.jpg?w=2000"
          alt="">
      </div>
      <div class="animals" @click="clickAnimal('horse')">
        <img
          src="https://img.freepik.com/premium-vector/cartoon-brown-horse-running-white-background_29190-5734.jpg?w=2000"
          alt="">
      </div>
      <!-- <div>
        {{ congrats }}
      </div> -->
      <div>
        <img v-show="fireworks"
          src="https://cliply.co/wp-content/uploads/2021/09/CLIPLY_372109170_FREE_FIREWORKS_400.gif" alt="">

        <audio controls autoplay>
          <source src="https://www.w3schools.com/tags/horse.ogg" type="audio/ogg">
          <source src="https://www.w3schools.com/tags/horse.mp3" type="audio/mpeg">
        </audio>
      </div>

      <h3>{{ congrats }}</h3>

    </div>

  </div>
</template>
<script>
export default {
  name: 'IdentifySounds',
  data() {
    return {
      congrats: '',
      isError: false,
      animalClicked: '',
      fireworks: false,
      clicks: 0,
      finalScore: 0,
      correctAnswer: 'horse'
    }
  },
  methods: {
    clickAnimal(answer) {
      this.animalClicked = answer
      if (answer === this.correctAnswer) {
        this.congrats = `You got it right! you've got ${this.score} points`
        this.fireworks = true
        setTimeout(() => {
          this.fireworks = false;
        }, 3000);
      } else {
        this.clicks += 1
        this.isError = true;
        this.congrats = `ooo oooh! this is a ${answer}!`
        setTimeout(() => {
          this.isError = false;
          this.congrats = ''
        }, 820);
      }
    }
  },
  computed: {
    score() {
      let points = 0
      let clicks = this.clicks
      if (clicks >= 10) {
        points = 10
      }
      else {
        points = ((10 - clicks) / 10 * 100)
      }
      return points
    }
  },
}
</script>


<style scoped>
.animals img {
  width: 100px;
  height: 100px;
  border: 1px solid black;
  cursor: pointer;
}

.animals {
  display: inline-block;
}

.oohh {
  animation: shake 0.5s;
  animation-iteration-count: infinite;
}

@keyframes shake {
  0% {
    transform: translate(1px, 1px) rotate(0deg);
  }

  10% {
    transform: translate(-1px, -2px) rotate(-1deg);
  }

  20% {
    transform: translate(-3px, 0px) rotate(1deg);
  }

  30% {
    transform: translate(3px, 2px) rotate(0deg);
  }

  40% {
    transform: translate(1px, -1px) rotate(1deg);
  }

  50% {
    transform: translate(-1px, 2px) rotate(-1deg);
  }

  60% {
    transform: translate(-3px, 1px) rotate(0deg);
  }

  70% {
    transform: translate(3px, 1px) rotate(-1deg);
  }

  80% {
    transform: translate(-1px, -1px) rotate(1deg);
  }

  90% {
    transform: translate(1px, 2px) rotate(0deg);
  }

  100% {
    transform: translate(1px, -2px) rotate(-1deg);
  }
}
</style>