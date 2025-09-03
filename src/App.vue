<template>
  <div class="app">
    <Navigation />
    <router-view />
    <Home />
    <UberMich />
    <Portfolio />
    <Kontakt />
  </div>
</template>

<script>
import Navigation from './components/Navigation.vue'
import Card from './components/Card.vue'
import Home from './views/Home.vue'
import UberMich from './views/UberMich.vue'
import Portfolio from './views/Portfolio.vue'
import Kontakt from './views/Kontakt.vue'
export default {
  name: 'App',
  components: {
    Navigation,
    Home,
    UberMich,
    Portfolio,
    Kontakt,
  },
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Raleway:wght@400;500&display=swap');
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: 'Raleway', sans-serif;
  font-weight: 400;
}

.app {
  min-height: 100vh;
  position: relative;
  background-color: #000;
}
.container {
  padding: 0 20px;
  max-width: 1140px;
  margin: 0 auto;
}
</style>
