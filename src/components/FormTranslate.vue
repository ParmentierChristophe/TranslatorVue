<template>
<div id="FormTranslate">
  <div class="columns is-centered">

    <form class="" v-on:submit="FormSubmit">

      <div class="field has-addons column">
        <p class="control">

          <span class="select">

        <select class="" v-model="language">
          <option selected value="en" >Anglais</option>
          <option value="ru">Russe</option>
          <option value="de">Allemand</option>
          <option value="zh">Chinois</option>
          <option value="ar">Arabe</option>
          <option value="es">Espagnol</option>
          <option value="uk">Ukrainien</option>


        </select>
      </span>
        </p>
        <p class="control">

          <input class="input" type="text" v-model="TextToTranslate" placeholder="Entrez votre texte">
        </p>
        <p class="control">
              <input class="button is-primary" type="submit" value="Translate">


        </p>
        </div>
    </form>
    </div>


  </div>
</template>

<script>
export default {
  name: 'FormTranslate',
  data() {
    return {
      TextToTranslate: '',
      language: ''
    }
  },
  created() {
    this.language = 'en';
  },
  methods: {
    FormSubmit(e) {
      this.$emit('formSubmit', this.TextToTranslate, this.language);
      e.preventDefault();

    }
  }
}
</script>

<style>
#FormTranslate {
  padding: 25px 0;
}
</style>
