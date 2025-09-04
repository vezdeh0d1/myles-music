<template>
  <div id="uber-mich" class="über-mich">
    <section class="hero">
      <div class="hero-text container">
        <h2>ÜBER MICH</h2>
        <div class="portrait">
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
  </div>
</template>

<script>
export default {
  name: 'UberMich',
  components: {},
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
  margin-bottom: 0;
  margin-left: clamp(12px, 5vw, 160px);

  /* Inner content */
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
    padding-inline: 10;

    gap: clamp(12px, 2.2vw, 28px);

    /* Titel */
    h2 {
      margin: 0;
      font-size: clamp(36px, 6vw, 56px);
      line-height: 1.1;
    }

    /* text */

    h3 {
      margin: 0;
      font-weight: 400;
      line-height: 1.6;
      font-size: clamp(14px, 1.6vw, 18px);
    }
  }

  .portrait {
    display: flex;
    justify-content: center;
    margin: 8px 0 4px;
    border-radius: 16px;
    border: 1px solid rgba(255, 255, 255, 0.25);
  }
  .portrait img {
    width: clamp(120px, 22vw, 260px);
    height: auto;
    display: block;
  }
}
</style>
