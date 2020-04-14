<template>
  <div id="app" :class="[this.warm, this.cold]">
    <transition name="fade" mode="out-in">
      <router-view />
    </transition>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {};
  },
  computed: {
    warm() {
      return typeof this.$store.state.weather.main != "undefined" &&
        this.$store.state.weather.main.temp > 15
        ? "warm"
        : "";
    },
    cold() {
      return typeof this.$store.state.weather.main != "undefined" &&
        this.$store.state.weather.main.temp < 15
        ? "cold"
        : "";
    }
  }
};
</script>

<style lang="scss">
.fade-enter-active,
.fade-leave-active {
  transition-duration: 1.3s;
  transition-property: opacity;
  transition-timing-function: ease;
}

.fade-enter,
.fade-leave-active {
  opacity: 0;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "montserrat", sans-serif;
}

#app {
  background-image: url("./assets/night-mountain.jpg");
  background-size: cover;
  background-position: bottom;
  transition: 0.7s;
  width: 100%;
}

#app.warm {
  background-image: url("./assets/warm-mountain.jpg");
  background-size: cover;
  background-position: bottom;
  transition: 0.7s;
  width: 100%;
}

#app.cold {
  background-image: url("./assets/cold-mountain.jpg");
  background-size: cover;
  background-position: bottom;
  transition: 0.7s;
  width: 100%;
}

main {
  min-height: 100vh;
  padding: 25px;
  background-image: linear-gradient(
    to bottom,
    rgba(0, 0, 0, 0.068),
    rgba(0, 0, 0, 0.288)
  );
}
</style>
