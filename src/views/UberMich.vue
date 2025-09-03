<template>
  <div class="über-mich">
    <section class="hero">
      <div class="hero-text container">
        <h2>ÜBER MICH</h2>
        <h3>Professional Electronic Music Experience</h3>
        <button>JETZT ANFANGEN</button>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: 'UberMich',
  components: {},
}
</script>

<style lang="scss" scoped>
.home {
  min-height: 100vh;
  position: relative;
}

.hero {
  background-color: #202020;
  height: 100vh;
  /* Rechter und linker Rand in Prozent. (10%)  */
  margin: 3vw 20vw 0 5vw; /* top | right | bottom | left */
  width: auto;
  /* border-radius: 8px; */
}

.hero {
  .hero-text {
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;

    color: #fff;

    h2 {
      font-size: 50px;
      @media (min-width: 550px) {
        font-size: 80px;
      }
    }

    hr:nth-child(2) {
      max-width: 365px;
      margin-bottom: 16px;
    }
    hr:nth-child(4) {
      height: 6px;
      background-color: #fff;
      border: none;
      max-width: 85px;
      margin-top: 16px;
    }
  }
}
</style>
