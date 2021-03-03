<template>
  <v-carousel v-model="model">
    <v-carousel-item v-for="(card, i) in cards" :key="card.id">
      <v-sheet color="color" height="100%" tile>
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
                    FLIP
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
                  <div class="pretext">Answer</div>
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
        </v-row>
      </v-sheet>
    </v-carousel-item>
  </v-carousel>
</template>

<script>
export default {
  name: "playground",
  data: () => ({
    cards: [
      {
        id: 1,
        frontText: "B",
        backText: "ऐ",
        colorClass: "red",
        flipped: false,
      },
      {
        id: 2,
        frontText: "C",
        backText: "ऐ",
        colorClass: "green",
        flipped: false,
      },
    ],
    model: 0,
    color: ["orange"],
  }),
  methods: {
    flipCard: function (card) {
      card.flipped = !card.flipped;
    },
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