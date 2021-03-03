<template>
  <v-container fill-height fluid>
    <v-carousel
      v-model="model"
      ref="myCarousel"
      hide-delimiters
      :touchless="true"
    >
      <div class="container text-center">
        <h2>English Alphabets!</h2>
      </div>

      <v-sheet color="yellow" elevation="3" height="100%" shaped>
        <v-carousel-item v-for="card in cards" :key="card.id">
          <v-row class="fill-height" align="center" justify="center">
            <div class="display-3">
              <div v-bind:class="card.colorClass" class="card card-front col">
                <transition name="flip">
                  <div
                    v-show="!card.flipped"
                    @click="flipCard(card)"
                    class="card-text card-front-text"
                  >
                    <div class="pretext"></div>
                    <h2>
                      {{ card.frontText }}
                    </h2>

                    <button class="button-white button-clear button-medium">
                      🔊
                      <i class="fas fa-sync-alt"></i>
                    </button>
                  </div>
                </transition>

                <transition name="flip">
                  <div
                    v-show="card.flipped"
                    @click="flipCard(card)"
                    class="card-text card-back-text"
                  >
                    <div class="pretext"></div>
                    <h2>
                      {{ card.backText }}
                    </h2>

                    <button class="button-white button-clear button-medium">
                      FLIP
                      <i class="fas fa-sync-alt"></i>
                    </button>
                  </div>
                </transition>
              </div>
            </div>
          </v-row> </v-carousel-item
      ></v-sheet>
    </v-carousel>
  </v-container>
</template>

<script>
export default {
  name: "playground",
  data: () => ({
    move: [],
    drag: false,
    touch: false,
    cards: [
      {
        id: 1,
        frontText: "A",
        backText: "ऐ",
        colorClass: "red",
        flipped: false,
      },
      {
        id: 2,
        frontText: "B",
        backText: "बी",
        colorClass: "orange",
        flipped: false,
      },
      {
        id: 3,
        frontText: "C",
        backText: "सी",
        colorClass: "blue",
        flipped: false,
      },
      {
        id: 4,
        frontText: "D",
        backText: "डी",
        colorClass: "green",
        flipped: false,
        sound: "",
      },
      {
        id: 5,
        frontText: "E",
        backText: "इ",
        colorClass: "purple",
        flipped: false,
        sound: "",
      },
      {
        id: 6,
        frontText: "F",
        backText: "ऍफ़",
        colorClass: "blue",
        flipped: false,
      },
      {
        id: 7,
        frontText: "G",
        backText: "जी",
        colorClass: "red",
        flipped: false,
        sound:
          "http://soundbible.com/mp3/Elevator Ding-SoundBible.com-685385892.mp3",
      },
      {
        id: 8,
        frontText: "H",
        backText: "एच",
        colorClass: "orange",
        flipped: false,
      },
      {
        id: 9,
        frontText: "I",
        backText: "ऑय",
        colorClass: "blue",
        flipped: false,
      },
      {
        id: 10,
        frontText: "J",
        backText: "जे",
        colorClass: "green",
        flipped: false,
        sound: "",
      },
      {
        id: 11,
        frontText: "K",
        backText: "के",
        colorClass: "purple",
        flipped: false,
        sound: "",
      },
      {
        id: 12,
        frontText: "L",
        backText: "एल",
        colorClass: "blue",
        flipped: false,
        sound: "",
      },
      {
        id: 13,
        frontText: "M",
        backText: "एम्",
        colorClass: "green",
        flipped: false,
        sound: "",
      },
      {
        id: 14,
        frontText: "N",
        backText: "ऍन",
        colorClass: "purple",
        flipped: false,
        sound: "",
      },
      {
        id: 15,
        frontText: "O",
        backText: "ओ",
        colorClass: "blue",
        flipped: false,
        sound: "",
      },
      {
        id: 16,
        frontText: "P",
        backText: "पी",
        colorClass: "green",
        flipped: false,
        sound: "",
      },
      {
        id: 17,
        frontText: "Q",
        backText: "क्यू",
        colorClass: "purple",
        flipped: false,
        sound: "",
      },
      {
        id: 18,
        frontText: "R",
        backText: "आर",
        colorClass: "blue",
        flipped: false,
        sound: "",
      },
      {
        id: 19,
        frontText: "S",
        backText: "ऐस",
        colorClass: "green",
        flipped: false,
        sound: "",
      },
      {
        id: 20,
        frontText: "T",
        backText: "टी",
        colorClass: "purple",
        flipped: false,
        sound: "",
      },
      {
        id: 21,
        frontText: "U",
        backText: "यू",
        colorClass: "blue",
        flipped: false,
        sound: "",
      },
      {
        id: 22,
        frontText: "V",
        backText: "डी",
        colorClass: "green",
        flipped: false,
        sound: "",
      },
      {
        id: 23,
        frontText: "W",
        backText: "डब्लू",
        colorClass: "purple",
        flipped: false,
        sound: "",
      },
      {
        id: 24,
        frontText: "X",
        backText: "एक्स",
        colorClass: "blue",
        flipped: false,
        sound: "",
      },
      {
        id: 25,
        frontText: "Y",
        backText: "व्हाई",
        colorClass: "purple",
        flipped: false,
        sound: "",
      },
      {
        id: 26,
        frontText: "Z",
        backText: "ज़ेड",
        colorClass: "blue",
        flipped: false,
        sound: "",
      },
    ],
    model: 0,
    colors: ["orange", "green"],
  }),
  methods: {
    flipCard: function (card) {
      this.playSound(`./audio/${card.id}.wav`);
      card.flipped = !card.flipped;
    },

    playSound(sound) {
      if (sound) {
        var audio = new Audio(sound);
        audio.play();
      }
    },

    logic(e) {
      let currentMove = this.touch ? e.touches[0].clientX : e.clientX;
      if (this.move.length === 0) {
        this.move.push(currentMove);
      }
      if (this.move[this.move.length - 1] - currentMove < -100) {
        this.$refs.myCarousel.$el
          .querySelector(".v-window__prev")
          .querySelector(".v-btn")
          .click();
        this.drag = false;
        this.touch = false;
      }
      if (this.move[this.move.length - 1] - currentMove > 100) {
        this.$refs.myCarousel.$el
          .querySelector(".v-window__next")
          .querySelector(".v-btn")
          .click();
        this.drag = false;
        this.touch = false;
      }
    },
  },
  mounted() {
    // For touch devices
    this.$refs.myCarousel.$el.addEventListener("touchmove", (e) => {
      this.drag = false;
      this.touch = true;
      this.logic(e);
    });
    window.addEventListener("touchend", (e) => {
      this.move = [];
    });

    // For non-touch devices
    this.$refs.myCarousel.$el.addEventListener("mousedown", (e) => {
      this.drag = true;
      this.touch = false;
      this.logic(e);
    });
    this.$refs.myCarousel.$el.addEventListener("mousemove", (e) => {
      this.drag ? this.logic(e) : null;
    });
    window.addEventListener("mouseup", (e) => {
      this.drag = false;
      this.touch = false;
      this.move = [];
    });
  },
};
</script>
<style scoped>
h1 {
  font-family: "Poppins", sans-serif;
  font-weight: 800;
  text-transform: uppercase;
  letter-spacing: 0.2em;
  color: #4e4e4e;
}

.container {
  max-width: 600px;
  margin: 0 auto;
}

.text-center {
  text-align: center;
}

.green {
  background-color: #084C61;
}

.red {
  background-color: #db4d52;
}

.yellow {
  background-color: #f9cf3b;
}

.blue {
  background-color: #49b0e4;
}

.purple {
  background-color: #996ce2;
}

/* Custom */

.button-white {
  background-color: white;
}

.button-white.button-clear {
  color: #000000;
  opacity: 0.2;
}

.button-large {
  font-size: 1.4rem;
  height: 4.5rem;
  line-height: 4.5rem;
  padding: 0 2rem;
}

.button-medium {
  font-size: 1.2rem;
  height: 2.5rem;
  line-height: 2.5rem;
  padding: 0 1rem;
}

ul.unstyled {
  list-style: none;
  padding: 0;
  margin: 0;
}

.card {
  transition: transform 0.5s;
  line-height: 1.5;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  width: 200px;
  height: 300px;
  padding: 4rem;
  border-radius: 5px;
  margin: 0 1rem;
}

.pretext {
  color: #000000;
  opacity: 0.2;
}

.card:hover {
  transform: scale(1.1);
}

.flex-grid-thirds {
  display: flex;
  justify-content: space-between;
}

.flex-grid-thirds .col {
  width: 32%;
}

.card-text h2 {
  color: #000000;
  opacity: 0.5;
  font-size: 6.2rem;
}

.flip-enter-active {
  transition: all 0.4s ease;
}

.flip-enter {
  transform: rotateY(180deg);
  opacity: 0;
}

.flip-leave {
  display: none;
}

.btn {
  outline: none !important;
}

.btn.btn-primary {
  background-color: #7652af;
  border-color: #7652af;
  outline: none;
  &:hover {
    background-color: darken(#7652af, 10%);
    border-color: darken(#7652af, 10%);
  }
  &:active,
  &:focus {
    background-color: lighten(#7652af, 5%);
    border-color: lighten(#7652af, 5%);
  }
  & .fa {
    padding-right: 4px;
  }
}

@media (max-width: 600px) {
  .flex-grid-thirds {
    display: block;
  }
  .flex-grid-thirds .col {
    width: 100%;
    margin: 0 0 10px 0;
  }
}
</style>