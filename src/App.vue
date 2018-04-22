<template>
  <div id="app">
    <h1>Translate A Word</h1>
    <translate-form v-on:formSubmit='translateText'></translate-form>
    <translate-output
      :translatedText='translatedText'>
    </translate-output>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'
export default {
  name: 'App',
  components: {
    TranslateForm,
    TranslateOutput
  },
  data () {
    return {
      translatedText: ''
    }
  },
  methods: {
    translateText (text, lang) {
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180422T141755Z.63539cf5ed44cba2.9deb9cfaa53fa95a0bdd191271e67ece44307025&lang=' + lang + '&text=' + text)
        .then((response) => {
          this.translatedText = response.body.text[0]
        })
    }
  }
}
</script>

<style>
  #app {
    text-align: center;
    font-family: 'Roboto', sans-serif;
    font-weight: 300;
  }
  input[type=text] {
    width: 25%;
    height: 2rem;
    padding-left: 1rem;
    border: none;
    border-bottom: 1px solid gainsboro;
  }
  input[type=submit]{
    width: 10%;
    background: rgba(56, 134, 235, 0.75);
    height: 2rem;
    color: #ffffff;
    font-weight: bolder;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background .5s;
  }
  input[type=submit]:hover {
    background: rgba(56, 134, 235,1.0);
  }

</style>
