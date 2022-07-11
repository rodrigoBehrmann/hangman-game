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
        title="Set a tip:"
        button="Play"
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
          :play="play"
          :playAgain="playAgain"
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
    },

    play: function(letter){
      //adiciona letra jogada
      this.letters.push(letter);

      this.verifyErrors(letter);
    },

    verifyErrors: function(letter){
      //acerto
      if(this.word.toLowerCase().indexOf(letter.toLowerCase()) >= 0 ){
        return this.verifyHits();
      }

      //erros
      this.errors++;

      //enforcado
      if(this.errors === 6){
        this.step = 'hanged';
      }
    },

    verifyHits: function(){
      let singleLetters = [...new Set(this.word.split(''))];
      if(singleLetters.length === (this.letters.length - this.errors)){
        this.step = 'winner';
      }
    },

    playAgain: function(){
      this.word = '',
      this.tip = '',
      this.errors = 0,
      this.letters = [],
      this.screen = 'home',
      this.step = 'word'
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
