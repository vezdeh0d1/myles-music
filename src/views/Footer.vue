<template>
  <div id="footer" class="footer">
    <section class="hero">
      <div class="hero-text container">
        <h1>🕶️ 📷 🎵 🎶</h1>
        <h6>© 2025 Myles Music: All rights reserved.</h6>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: 'Footer',
}
</script>

<style lang="scss" scoped>
.home {
  min-height: 100vh;
  position: relative;
}

.hero {
  background-color: #0e0e0e;
  height: 20vh;
  margin: 0 10vw;
  width: auto;

  .hero-text {
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    color: #d9d9d9;

    h1 {
      font-size: clamp(20px, 5vw, 30px);
      margin-bottom: 20px;
    }
  }
}
</style>
