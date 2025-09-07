<template>
  <div id="galerie" class="Portfolio">
    <section class="hero">
      <div class="hero-text">
        <h2>PORTFOLIO</h2>

        <div class="gallery">
          <div
            v-for="(item, i) in items"
            :key="i"
            class="portrait"
            role="button"
            tabindex="0"
            @click="openLightbox(item)"
          >
            <div class="thumb">
              <img :src="item.poster" :alt="item.alt" loading="lazy" decoding="async" />
              <span class="play-badge">▶</span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Lightbox -->
    <div
      v-if="lightbox"
      class="lightbox"
      role="dialog"
      aria-modal="true"
      :aria-label="selected?.alt || 'Full size Video'"
      @click="closeLightbox"
    >
      <video
        v-if="selected"
        ref="player"
        :src="selected.src"
        controls
        autoplay
        playsinline
        class="player"
        @click.stop
      ></video>
      <button class="lightbox-close" @click.stop="closeLightbox" aria-label="Close">×</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Portfolio',
  data: () => ({
    lightbox: false,
    selected: null,
    _lastFocus: null,
    items: [
      {
        src: new URL('../assets/vid1.mp4', import.meta.url).href,
        poster: new URL('../assets/poster1.jpg', import.meta.url).href,
        alt: 'Clip 1',
      },
      {
        src: new URL('../assets/vid2.mp4', import.meta.url).href,
        poster: new URL('../assets/poster2.jpg', import.meta.url).href,
        alt: 'Clip 2',
      },
      {
        src: new URL('../assets/vid3.mp4', import.meta.url).href,
        poster: new URL('../assets/poster3.jpg', import.meta.url).href,
        alt: 'Clip 3',
      },
      {
        src: new URL('../assets/vid4.mp4', import.meta.url).href,
        poster: new URL('../assets/poster4.jpg', import.meta.url).href,
        alt: 'Clip 4',
      },
      {
        src: new URL('../assets/vid5.mp4', import.meta.url).href,
        poster: new URL('../assets/poster5.jpg', import.meta.url).href,
        alt: 'Clip 5',
      },
      {
        src: new URL('../assets/vid6.mp4', import.meta.url).href,
        poster: new URL('../assets/poster6.jpg', import.meta.url).href,
        alt: 'Clip 6',
      },
    ],
  }),

  methods: {
    openLightbox(item) {
      if (this.lightbox) return
      this._lastFocus = document.activeElement
      this.selected = item
      this.lightbox = true
      document.body.style.overflow = 'hidden'
      window.addEventListener('keydown', this.onEsc)
    },
    closeLightbox() {
      if (!this.lightbox) return
      this.lightbox = false
      this.selected = null
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
.hero {
  background-color: #0e0e0e;
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
    border-radius: 16px;
    border: 1px solid rgba(255, 255, 255, 0.25);
    cursor: pointer;
    transition: transform 0.18s ease;
    background: rgba(255, 255, 255, 0.02);
  }
  .portrait:hover {
    transform: translateY(-6px);
  }

  .thumb {
    position: relative;
  }
  .thumb img {
    width: 100%;
    height: auto;
    display: block;
    border-radius: 12px;
  }
  .play-badge {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    font-size: 32px;
    line-height: 1;
    color: rgba(255, 255, 255, 0.95);
    text-shadow: 0 2px 8px rgba(0, 0, 0, 0.5);
    pointer-events: none;
  }
}

.lightbox {
  position: fixed;
  inset: 0;
  z-index: 1000;
  background: rgba(0, 0, 0, 0.9);
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 4vw;
}
.player {
  max-width: 90vw;
  max-height: 90vh;
  border-radius: 12px;
  background: #0e0e0e;
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

@supports (height: 100svh) {
  .hero {
    min-height: 100svh;
  }
  .player {
    max-height: 90svh;
  }
}
</style>
