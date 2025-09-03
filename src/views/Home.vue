<template>
  <div class="home">
    <section class="hero">
      <div class="hero-text container">
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
    // Sanfter Scroll zum Kontakt-Block
    scrollToKontakt() {
      const el = document.getElementById('kontakt')
      if (el) el.scrollIntoView({ behavior: 'smooth', block: 'start' })
    },
  },
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
  margin: 0 10vw;
  width: auto;

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

    /* NEW: интерактивная кнопка */
    button {
      margin-top: 12px;
      padding: 10px 18px;
      background: transparent;
      color: #f28c3c;
      border: 1px solid currentColor;
      border-radius: 2px;

      cursor: pointer; /* курсор-рука */
      transition:
        color 0.18s ease,
        border-color 0.18s ease,
        background-color 0.18s ease,
        transform 0.05s ease; /* лёгкий клик */
    }

    /* NEW: hover/focus — чуть подсветить */
    button:hover,
    button:focus-visible {
      background-color: rgba(242, 140, 60, 0.12); /* лёгкая оранжевая вуаль */
      color: #ff9a4d;
      border-color: #ff9a4d;
      outline: none;
    }

    /* NEW: нажата — чуть «утопить» */
    button:active {
      transform: translateY(1px);
    }
  }
}
</style>
