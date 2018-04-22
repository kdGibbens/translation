<template>
  <div class="translate-form">
      <form v-on:submit.prevent="formSubmit">
          <input type="text" v-model="textToTranslate" placeholder="Enter a word...">
          <select v-model='lang'>
              <option value="ru">Russian</option>
              <option value="es">Spanish</option>
              <option value="fr">French</option>
              <option value="zh">Chinese</option>
          </select>
          <input type="submit" value="Translate">
      </form>
  </div>
</template>

<script>
export default {
  name: 'translate-form',
  data () {
    return {
      textToTranslate: '',
      lang: ''
    }
  },
  methods: {
    formSubmit () {
      this.$emit('formSubmit', this.textToTranslate, this.lang)
    }
  },
  created () {
    this.lang = 'ru'
  }
}
</script>

<style>

</style>
