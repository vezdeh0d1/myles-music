<template>
  <header :class="{ 'scrolled-nav': scrolledNav }">
    <nav>
      <div class="branding">
        <h1>MYLES MUSIC</h1>
      </div>

      <ul class="navigation">
        <li>
          <router-link class="link" :to="{ name: 'Home' }" @click="scrollToHome">Home</router-link>
        </li>
        <li>
          <router-link class="link" :to="{ name: 'Über mich' }" @click="scrollToUberMich"
            >Über mich</router-link
          >
        </li>
        <li>
          <router-link class="link" :to="{ name: 'Galerie' }" @click="scrollToGalerie"
            >Galerie</router-link
          >
        </li>
        <li>
          <router-link class="link" :to="{ name: 'Kontakt' }" @click="scrollToKontakt"
            >Kontakt</router-link
          >
        </li>
      </ul>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'Navigation',
  data() {
    return {
      scrolledNav: false,
    }
  },
  mounted() {
    window.addEventListener('scroll', this.updateScroll, { passive: true })
    this.updateScroll()
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.updateScroll)
  },

  methods: {
    updateScroll() {
      const scrollPosition = window.scrollY
      if (scrollPosition > 50) {
        this.scrolledNav = true
        return
      }
      this.scrolledNav = false
    },
    scrollToHome() {
      const el = document.getElementById('home')
      if (el) el.scrollIntoView({ behavior: 'smooth', block: 'start' })
    },
    scrollToUberMich() {
      const el = document.getElementById('uber-mich')
      if (el) el.scrollIntoView({ behavior: 'smooth', block: 'start' })
    },
    scrollToGalerie() {
      const el = document.getElementById('galerie')
      if (el) el.scrollIntoView({ behavior: 'smooth', block: 'start' })
    },
    scrollToKontakt() {
      const el = document.getElementById('kontakt')
      if (el) el.scrollIntoView({ behavior: 'smooth', block: 'start' })
    },
  },
}
</script>

<style lang="scss" scoped>
header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 99;
  background-color: rgba(0, 0, 0, 0.8);
  color: #fff;

  transition:
    background-color 0.35s ease 0.08s,
    box-shadow 0.35s ease 0.08s;
}

header nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin: 0 20vw; /* Rechter und linker Rand in Prozent. (20%)  */
  padding: 12px 0;
  transition: padding 0.35s ease 0.08s;
}

.branding h1 {
  margin: 0;
  line-height: 1;
}

.navigation {
  display: flex;
  align-items: center;
  gap: 24px; /* "gap" zwischen Home / About / ... */
  list-style: none;
  margin: 0;
  padding: 0;
}

.link {
  color: #fff;
  font-weight: 500;
  font-size: 14px;
  text-decoration: none;
  padding-bottom: 4px;
  border-bottom: 1px solid transparent;
  transition:
    color 0.2s ease,
    border-color 0.2s ease;

  cursor: pointer;

  &:hover {
    color: #5b5897;
    border-color: #686699;
  }
}

:global(main) {
  padding-top: 56px;
}

.scrolled-nav {
  background-color: #000;
  box-shadow:
    0 4px 6px -1px rgba(0, 0, 0, 0.1),
    0 2px 4px -1px rgba(0, 0, 0, 0.06);

  nav {
    padding: 8px 0;
  }
}
</style>
