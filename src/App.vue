<script setup>
  import { ref } from 'vue'

  const longUrl = ref('')
  const shortUrl = ref('')

  const API_URL = 'https://api-ssl.bitly.com/v4/shorten'
  const BITLY_TOKEN = 'a41a9bb5b958a71e470c0448831a620f90bb137b'

  function shortenLink() {
    fetch(API_URL, {
      method: 'POST',
      headers: {
        'Authorization': `Bearer ${BITLY_TOKEN}`,
        'Content-Type': 'application/json'
      },
      body: JSON.stringify({
        'long_url': longUrl.value,
        'domain': 'bit.ly'
      })
    })
      .then(response => {
        if (response.ok) {
          return response.json()
        }
        throw new Error("Could not fetch resource")
      })
      .then(data => shortUrl.value = data.link)
      .catch(error => console.error(error))
  };
</script>

<template>
  <div class="wrap">
    <main>
      <img class="hero" src="/src/assets/images/hero.png" alt="hero graphic">
      <section class="interaction-section">
        <h1>Link Shortener</h1>
        <form class="action-area" form="shortener">
          <input v-model="longUrl" class="action__input" type="url" name="long-link"
            placeholder="https://example.com/loooooong/url" autofocus required>
          <button @click="shortenLink" class="action__btn" type="button">Shorten</button>
        </form>
        <div class="result-area">
          <label for="short-link">Shortened Link:</label>
          <output class="short-link" id="short-link" form="shortener">{{ shortUrl }}</output>
        </div>
      </section>
    </main>
  </div>
</template>