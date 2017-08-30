<template>
<div id="app">
  <section class="hero is-primary">
    <div class="hero-body">
      <div class="container">
        <h1 class="title is-1 has-text-centered">
        Traduction
      </h1>
        <h2 class="subtitle has-text-centered">
        App with Vue.js
      </h2>
      </div>
    </div>
  </section>

  <FormTranslate v-on:formSubmit="translateText"></FormTranslate>
  <OutputTranslate v-text='translatedText'></OutputTranslate>

  <footer class="footer back">
    <div class="container">
      <div class="content has-text-centered">
        <p>
          by <a target="_blank" href="http://christophe-parmentier.fr">Crispy</a>.
          <p>
            <a class="icon" target="_blank" href="https://github.com/ParmentierChristophe">
            <i class="fa fa-github"></i>
          </a>
          </p>
      </div>
    </div>
  </footer>
</div>
</template>

<script>
import FormTranslate from './components/FormTranslate'
import OutputTranslate from './components/OutputTranslate'


export default {
  name: 'app',
  components: {
    FormTranslate,
    OutputTranslate
  },
  data: function() {
    return {
      translatedText: ''
    }
  },
  methods: {
    translateText: function(text, language) {
      this.$http.get("https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170821T092823Z.6e0660cadc212afd.f70662378a66709815058857d9c0547f3874e013&lang=fr-" + language + "&text=" + text).then((response) => {
        this.translatedText = response.body.text[0];

      });
    }
  }
}
</script>

<style>
html {
  height: 100%;
}

body {
  min-height: 100%;
  margin: 0;
  padding: 0;
  position: relative;
}

.back {
  width: 100%;
  position: absolute;
  bottom: 0;
}
</style>
