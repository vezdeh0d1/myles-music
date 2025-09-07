<template>
  <div class="app">
    <Navigation />
    <Home />
    <UberMich />
    <Portfolio />
    <Kontakt />
    <Footer />
  </div>
</template>

<script>
import Navigation from './components/Navigation.vue'
import Home from './views/Home.vue'
import UberMich from './views/UberMich.vue'
import Portfolio from './views/Portfolio.vue'
import Kontakt from './views/Kontakt.vue'
import Footer from './views/Footer.vue'
export default {
  name: 'App',
  components: {
    Navigation,
    Home,
    UberMich,
    Portfolio,
    Kontakt,
    Footer,
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
  background-color: #0e0e0e;
}
.container {
  padding: 0 20px;
  max-width: 1140px;
  margin: 0 auto;
}
</style>
