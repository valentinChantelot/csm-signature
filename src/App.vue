<template>
  <div id="app">
    <Formulaire />
  </div>
</template>

<script>
import Formulaire from "./components/Formulaire.vue";

export default {
  name: "app",
  components: {
    Formulaire
  }
};
</script>

<style lang="scss">
body {
  margin: 0;
  padding: 0;

  background: #0d3a58;
}
#app {
  min-height: 100vh;
}
.orange,
.pink,
.blue,
.yellow {
  font-weight: bold;
}

.orange {
  color: #ff9d00;
}

.pink {
  color: #fb94ff;
}

.yellow {
  color: #ffc600;
}

.blue {
  color: #9effff;
}

.hidden {
  display: none;
}

.displayed {
  display: block;
}
</style>
