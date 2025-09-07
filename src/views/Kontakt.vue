<template>
  <div id="kontakt" class="Kontakt">
    <section class="hero">
      <div class="hero-text container">
        <h2>KONTAKT</h2>

        <!-- form -->
        <form class="form" @submit.prevent="notification">
          <div class="field">
            <label for="name">NAME</label>
            <input
              id="name"
              v-model="form.name"
              type="text"
              autocomplete="name"
              placeholder="Ihr Name"
            />
          </div>

          <div class="field">
            <label for="email">E-MAIL</label>
            <input
              id="email"
              v-model="form.email"
              type="email"
              autocomplete="email"
              placeholder="name@example.com"
            />
          </div>

          <div class="field">
            <label for="tel">TELEFON</label>
            <input
              id="tel"
              v-model="form.tel"
              type="tel"
              inputmode="tel"
              autocomplete="tel"
              placeholder="+49 …"
            />
          </div>

          <div class="field">
            <label for="details">EVENT-DETAILS</label>
            <input
              id="details"
              v-model="form.details"
              type="text"
              placeholder="Art, Ort, Gästezahl …"
            />
          </div>

          <div class="field">
            <label for="date">DATUM</label>
            <input id="date" v-model="form.date" type="date" />
          </div>

          <div class="field">
            <label for="msg">NACHRICHT</label>
            <textarea
              id="msg"
              v-model="form.message"
              rows="4"
              placeholder="Ihre Nachricht"
            ></textarea>
          </div>

          <div class="actions">
            <button type="submit">ANFRAGE SENDEN</button>
          </div>
        </form>
      </div>
    </section>

    <!-- toast notification -->
    <transition name="toast">
      <div v-if="toastVisible" class="toast" role="status" aria-live="polite">
        Vielen Dank für Ihre Anfrage.
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  name: 'Kontakt',
  data: () => ({
    form: {
      name: '',
      email: '',
      tel: '',
      details: '',
      date: '',
      message: '',
    },
    toastVisible: false,
    _toastTimer: null,
  }),
  methods: {
    notification() {
      // form to the server would go here
      this.toastVisible = true
      clearTimeout(this._toastTimer)
      this._toastTimer = setTimeout(() => (this.toastVisible = false), 2500)
    },
  },
  beforeUnmount() {
    clearTimeout(this._toastTimer)
  },
}
</script>

<style lang="scss" scoped>
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
      font-size: 50px;
      @media (min-width: 550px) {
        font-size: 80px;
      }
    }

    /* FORM */
    .form {
      width: 100%;
      text-align: left;
      display: flex;
      flex-direction: column;
      gap: clamp(12px, 2.2vw, 20px);
    }

    .field {
      display: flex;
      flex-direction: column;
      gap: 8px;
    }

    label {
      text-transform: uppercase;
      letter-spacing: 0.03em;
      font-size: clamp(14px, 1.2vw, 16px);
      color: #e5e5e5;
    }

    input,
    textarea {
      width: 100%;
      color: #fff;
      background: rgba(255, 255, 255, 0.04);
      border: 1px solid rgba(255, 255, 255, 0.25);
      border-radius: 8px;
      padding: 10px 12px;
      outline: none;
      transition:
        border-color 0.18s ease,
        background-color 0.18s ease,
        box-shadow 0.18s ease;
    }

    input::placeholder,
    textarea::placeholder {
      color: #a8a8a8;
    }

    input:focus,
    textarea:focus {
      background-color: rgba(255, 255, 255, 0.08);
      border-color: #ff9a4d;
      box-shadow: 0 0 0 3px rgba(255, 154, 77, 0.2);
    }

    .actions {
      margin-top: 4px;
    }

    button {
      display: block;
      margin: 12px auto 20px; /* top | left/right(auto) | bottom */
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

/* toast */
.toast {
  position: fixed;
  bottom: 24px;
  left: 50%;
  transform: translateX(-50%);
  z-index: 1001;
  background: #1f2937;
  color: #fff;
  padding: 10px 14px;
  border-radius: 10px;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.35);
  pointer-events: none;
  font-size: 14px;
}
.toast-enter-active,
.toast-leave-active {
  transition: opacity 0.2s ease;
}
.toast-enter-from,
.toast-leave-to {
  opacity: 0;
}
</style>
