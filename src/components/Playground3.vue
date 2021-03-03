<template>
  <v-container>
    <div class="heading">
      <h1>Play Sound</h1>
      <h4>Playing audio files with Vue.js</h4>
    </div>

    <div class="container" id="app">
      <div class="form-group">
        <label>
          <button
            class="btn btn-primary btn-sm"
            @click.prevent="playSound(`./audio/1.wav`)"
          >
            <span class="fa fa-play-circle-o"></span>
          </button>
          Play Air Plane Ding
        </label>
        <br />
        <label>
          <button
            class="btn btn-primary btn-sm"
            @click.prevent="
              playSound(
                'http://soundbible.com/mp3/Elevator Ding-SoundBible.com-685385892.mp3'
              )
            "
          >
            <span class="fa fa-play-circle-o"></span>
          </button>
          Play Elevator Ding
        </label>
        <br />
        <label>
          <button
            class="btn btn-primary btn-sm"
            @click.prevent="somesound(`../assets/1.wav`)"
          >
            <span class="fa fa-play-circle-o"></span>
          </button>
          Play from local
        </label>
      </div>
    </div>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      text: "",
    };
  },
  methods: {
    playSound(sound) {
      if (sound) {
        var audio = new Audio(sound);
        audio.play();
      }
    },

    somesound(sound) {},
  },
};
</script>

