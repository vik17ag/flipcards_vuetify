<template>
  <v-app>
    <v-content>
      <playground></playground>
    </v-content>
  </v-app>
</template>

<script>
import Playground from "./components/Playground3";

export default {
  name: "App",
  components: {
    Playground,
  },
};
</script>

