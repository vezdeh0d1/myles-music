<template>
  <div id="uber-mich" class="über-mich">
    <section class="hero">
      <div class="hero-text container">
        <h2>ÜBER MICH</h2>

        <div class="portrait" role="button" tabindex="0" @click="openLightbox">
          <img
            src="@/assets/professional-portrait.jpg"
            alt="Professional portrait"
            loading="lazy"
          />
        </div>

        <h3>
          Mit über zehn Jahren Erfahrung in der elektronischen Musikszene verstehe ich es, durch
          präzise Musikauswahl und nahtlose Übergänge eine einzigartige Atmosphäre zu schaffen. Mein
          Fokus liegt auf der perfekten Balance zwischen energiegeladenen Beats und melodischen
          Klanglandschaften.
        </h3>
        <h3>
          Von eleganten Corporate Events bis hin zu ausgelassenen Clubnächten – ich passe meinen
          Sound individuell an jeden Anlass an. Dabei setze ich auf eine Kombination aus klassischen
          House-Elementen und zeitgenössischen Electronic-Produktionen, die sowohl Kenner als auch
          ein breites Publikum begeistern.
        </h3>
        <h3>
          Professionalität, Zuverlässigkeit und die Leidenschaft für außergewöhnliche Musik stehen
          im Mittelpunkt meiner Arbeit. Lassen Sie uns gemeinsam Ihr Event zu einem unvergesslichen
          Erlebnis machen.
        </h3>
      </div>
    </section>

    <div
      v-if="lightbox"
      class="lightbox"
      role="dialog"
      aria-modal="true"
      aria-label="Full size photo"
      @click="closeLightbox"
    >
      <img src="@/assets/professional-portrait.jpg" alt="Professional portrait – big" @click.stop />
      <button class="lightbox-close" @click.stop="closeLightbox" aria-label="Close">×</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'UberMich',
  data: () => ({ lightbox: false }),

  methods: {
    openLightbox() {
      if (this.lightbox) return
      this.lightbox = true
      document.body.style.overflow = 'hidden'
      window.addEventListener('keydown', this.onEsc)
    },
    closeLightbox() {
      if (!this.lightbox) return
      this.lightbox = false
      document.body.style.overflow = ''
      window.removeEventListener('keydown', this.onEsc)
    },
    onEsc(e) {
      if (e.key === 'Escape') this.closeLightbox()
    },
  },

  beforeUnmount() {
    window.removeEventListener('keydown', this.onEsc)
    document.body.style.overflow = ''
  },
}
</script>

<style lang="scss" scoped>
#uber-mich {
  scroll-margin-top: 72px;
}

.hero {
  background-color: #202020;
  min-height: 100vh;

  margin-top: clamp(12px, 3vw, 48px);
  margin-right: clamp(24px, 20vw, 320px);
  margin-left: clamp(12px, 5vw, 160px);

  .hero-text {
    height: 100%;
    display: flex;
    flex-direction: column;
    padding-top: clamp(16px, 5vh, 120px);
    align-items: center;
    text-align: center;
    color: #d9d9d9;
    width: 100%;
    max-width: 68ch;
    gap: clamp(12px, 2.2vw, 28px);

    h2 {
      margin: 0;
      font-size: clamp(36px, 6vw, 56px);
      line-height: 1.1;
    }
    h3:last-of-type {
      margin-bottom: clamp(24px, 8vh, 120px);
    }
  }

  .portrait {
    display: flex;
    justify-content: center;
    margin: 8px 0 4px;
    border-radius: 16px;
    border: 1px solid rgba(255, 255, 255, 0.25);
    cursor: pointer;
    transition: transform 0.18s ease;
  }
  .portrait:hover {
    transform: translateY(-6px);
  }
  .portrait img {
    width: clamp(120px, 22vw, 260px);
    height: auto;
    display: block;
    border-radius: 12px;
  }
}

.lightbox {
  position: fixed;
  inset: 0;
  z-index: 1000;
  background: rgba(0, 0, 0, 0.88);
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 4vw;
}
.lightbox img {
  max-width: 90vw;
  max-height: 90vh;
  object-fit: contain;
  border-radius: 12px;
}
.lightbox-close {
  position: fixed;
  top: 16px;
  right: 20px;
  font-size: 28px;
  color: #fff;
  background: transparent;
  border: 0;
  cursor: pointer;
}
</style>
