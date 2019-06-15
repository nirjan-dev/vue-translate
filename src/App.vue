<template>
  <div class="text-center mt-4" id="app">
      <h1>Word Translator</h1>
      <h3>Powerd by Vue.js</h3>
      <TranslateForm class="mt-5" @formSubmit="translateText"></TranslateForm>
      <TranslateOutput>{{ translatedText }}</TranslateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'
export default {
  name: 'App',
  components: {
    TranslateForm,
    TranslateOutput,
  },
  data(){
    return {
      translatedText: '',
    }
  },
  methods: {
    translateText(text,language){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180710T023712Z.b74875a971136f2a.04277a1b16c9aab6aa9ff0de4ae1c7bf02a800d2&lang=' + language + '&text=' + text)
        .then((result) => {
          this.translatedText = result.data.text[0];
        }).catch((err) => {
          console.error(err);
        });
    }
  }
}
</script>

<style>
  body{
    background: #fefefe;
    overflow: hidden;
  }
  body,html{
    padding: 0;
    margin: 0;
  }
</style>
