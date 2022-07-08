<template>
  <div id="app">
      <h1>Hangman Game</h1>

      <section v-if="screen === 'home'" id="home">

        <Formulario v-if="step === 'word'"
        title="Type a word:"
        button="Next"
        :action="setWord"
        />

        <Formulario v-if="step === 'tip'"
        title="Defina a dica"
        button="Iniciar Jogo"
        :action="setTip"

        />

      </section>

      <section v-if="screen === 'game'" id="game">
        <Game 
          :errors="errors"
          :word="word"
          :tip="tip"
          :verifyLetter="verifyLetter"
          :step="step"
          :letters="letters"
        />
      </section>

  </div>
</template>

<script>
import './css/global.css';

import Formulario from './components/Formulario';
import Game from './components/Game';


export default {
  name: 'App',
  data(){
    return {
      screen: 'home',
      step:'word',
      word: '',
      tip: '',
      errors: 0,
      letters:[]
    }
  },
  components: {
    Formulario,
    Game
  },
  methods:{
    setWord: function(word){
      this.word = word;
      this.step = 'tip'
    },

    setTip: function(tip){
      this.tip = tip;
      this.screen = 'game';
      this.step = 'game';
    },

    verifyLetter: function(letter){
      return this.letters.find(item => item.toLowerCase() === letter.toLowerCase());
    }

  }
}
</script>

<style>
#app {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>
