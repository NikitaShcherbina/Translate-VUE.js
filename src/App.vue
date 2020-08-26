<template>
  <div class='text-center' id="app">
    <h1>Word Translator</h1>
    <h5>Power By Vue.Js</h5>
    <link rel='stylesheet' href='https://bootswatch.com/3/paper/bootstrap.min.css'>
    <TranslateForm @formSubmit='translateText'></TranslateForm>
    <TranslateOutput v-text='transletedText'></TranslateOutput>
  </div>
</template>

<script>
  import TranslateForm from './components/TranslateForm';
  import TranslateOutput from './components/TranslateOutput';
  import translate from 'google-translate-open-api';

  export default {
    name: 'app',
    components: {
      TranslateForm,
      TranslateOutput
    },
    data: function() {
      return {
        transletedText: '' 
      }
    },
    methods: { 
     async translateText(text, language) {
      const result = await translate(text, {
     tld: 'com',
     to: language
    });
    this.transletedText = result.data[0];
      }
    }
  }
</script>

<style>
body {
  background: #fefefe;
}
</style>





