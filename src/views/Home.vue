<template>
  <div id="home">
    <section class="hero">
      <div class="hero-text">
        <h2>MYLES MUSIC</h2>
        <h3>Professional Electronic Music Experience</h3>
        <button type="button" @click="scrollToKontakt">JETZT ANFRAGEN</button>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: 'Home',
  methods: {
    // Scroll to Kontakt-Block
    scrollToKontakt() {
      const el = document.getElementById('kontakt')
      if (el) el.scrollIntoView({ behavior: 'smooth', block: 'start' })
    },
  },
}
</script>

<style lang="scss" scoped>
.hero {
  background-color: #202020;
  min-height: 100vh;
  margin: 0 10vw;

  .hero-text {
    min-height: inherit;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    color: #d9d9d9;

    h2 {
      margin: 0;
      font-size: 60px;
    }

    h3 {
      margin: 0;
      font-weight: 400;
    }

    button {
      display: block;
      margin: 12px auto 12px;
      padding: 10px 18px;
      background: transparent;
      color: #f28c3c;
      border: 1px solid currentColor;
      border-radius: 2px;
      cursor: pointer;
      transition:
        color 0.18s ease,
        border-color 0.18s ease,
        background-color 0.18s ease,
        transform 0.05s ease;
    }

    button:hover,
    button:focus-visible {
      background-color: rgba(242, 140, 60, 0.12);
      color: #ff9a4d;
      border-color: #ff9a4d;
      outline: none;
    }

    button:active {
      transform: translateY(1px);
    }
  }
}
</style>
