<template>
  <div id="app">
    <h2>在线翻译</h2>
    <h5 class="text-muted">简单 / 易用 / 便捷</h5>
    <translateForm v-on:formSubmit="translateText"></translateForm>
    <translateOutput v-text="translatedText"></translateOutput>
  </div>
</template>

<script>

import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'App',
  data() {
    return {
      translatedText:""
    }
  },
  components: {
    TranslateForm,TranslateOutput
  },
  methods: {
    translateText:function(text,language){
      // alert(text);
      this.$http.get(''+text).then((response)=>{
        //console.log(response.body.text[0]);
        this.translatedText = response.body.text[0];
      })
    }
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
