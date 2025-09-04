<template>
  <div id="galerie" class="Portfolio">
    <section class="hero">
      <div class="hero-text container">
        <h2>PORTFOLIO</h2>

        <div class="gallery">
          <div
            v-for="(img, i) in images"
            :key="i"
            class="portrait"
            role="button"
            tabindex="0"
            @click="openLightbox(img.src, img.alt)"
            @keydown.enter="openLightbox(img.src, img.alt)"
          >
            <img :src="img.src" :alt="img.alt" loading="lazy" decoding="async" />
          </div>
        </div>
      </div>
    </section>

    <div
      v-if="lightbox"
      class="lightbox"
      role="dialog"
      aria-modal="true"
      :aria-label="selectedAlt || 'Bild in voller Größe'"
      @click="closeLightbox"
    >
      <img :src="selectedSrc" :alt="selectedAlt || 'Bild – groß'" @click.stop />
      <button class="lightbox-close" @click.stop="closeLightbox" aria-label="Close">×</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Portfolio',
  data: () => ({
    lightbox: false,
    selectedSrc: null,
    selectedAlt: '',
    images: [
      {
        src: new URL('../assets/professional-portrait.jpg', import.meta.url).href,
        alt: 'Professional portrait',
      },
      { src: new URL('../assets/pic1.jpg', import.meta.url).href, alt: 'pic1' },
      { src: new URL('../assets/pic2.jpg', import.meta.url).href, alt: 'pic2' },
      { src: new URL('../assets/pic3.jpg', import.meta.url).href, alt: 'pic3' },
      { src: new URL('../assets/pic4.jpg', import.meta.url).href, alt: 'pic4' },
      { src: new URL('../assets/pic5.jpg', import.meta.url).href, alt: 'pic5' },
    ],
  }),

  methods: {
    openLightbox(src, alt) {
      if (this.lightbox) return
      this.selectedSrc = src
      this.selectedAlt = alt || ''
      this.lightbox = true
      document.body.style.overflow = 'hidden'
      window.addEventListener('keydown', this.onEsc)
    },
    closeLightbox() {
      if (!this.lightbox) return
      this.lightbox = false
      this.selectedSrc = null
      this.selectedAlt = ''
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
#galerie {
  scroll-margin-top: 72px;
}
.hero {
  background-color: #000000;
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
    max-width: clamp(720px, 90vw, 1200px);
    gap: clamp(12px, 2.2vw, 28px);

    h2 {
      margin: 0;
      font-size: clamp(36px, 6vw, 56px);
      line-height: 1.1;
    }
  }

  .gallery {
    width: 100%;
    display: grid;
    grid-template-columns: repeat(3, minmax(0, 1fr));
    gap: 24px;
  }

  .portrait {
    display: flex;
    justify-content: center;
    border-radius: 16px;
    border: 1px solid rgba(255, 255, 255, 0.25);
    cursor: pointer;
    transition: transform 0.18s ease;
    background: rgba(255, 255, 255, 0.02);
  }
  .portrait:hover {
    transform: translateY(-6px);
  }

  .portrait img {
    width: 100%;
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
