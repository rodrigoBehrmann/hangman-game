<template>
    <div class="game">

        <Gibbet 
        :errors="errors"
        />

        <Word 
            :word="word"
            :tip="tip"
            :verifyLetter="verifyLetter"
            :step="step"
        />

        <KeyBoard
            v-if="step === 'game'"
            :letters="letters"
            :verifyLetter="verifyLetter"
            :play="play"
        />

        <Final 
            v-if="step != 'game'"
            :step="step"
            :text="step === 'winner' ? 'Congratulations :)' : 'Game Over :('"
            :playAgain="playAgain"
        />

    </div>
</template>



<script>

import Gibbet from './Gibbet';
import Word from './Word';
import KeyBoard from './KeyBoard';
import Final from './Final';

export default{
    name: 'GameItem',
    props:{
        errors: Number,
        word: String,
        tip: String,
        verifyLetter: Function,
        step: String,
        letters: Array,
        play: Function,
        playAgain: Function
    },
    data(){
        return{
            
        }
    },
    methods: {
        
    },
    components:{
        Gibbet,
        Word,
        KeyBoard,
        Final
    }
}
</script>


<style>
   
   .game{
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
   }

</style>
