<script setup>
</script>

<template>
  <div class="wrap">
    <main>
      <img class="hero" src="/src/assets/images/hero.png" alt="hero graphic">
      <section class="interaction-section">
        <h1>Link Shortener</h1>
        <form class="action-area" form="shortener">
          <input class="action__input" type="url" name="long-link"
            placeholder="https://example.com/loooooong/url" autofocus required>
          <button class="action__btn" type="button">Shorten</button>
        </form>
        <div class="result-area">
          <label for="short-link">Shortened Link:</label>
          <output class="short-link" id="short-link" form="shortener"></output>
        </div>
      </section>
    </main>
  </div>
</template>