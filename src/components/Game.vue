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
            :letters="letters"
            :verifyLetter="verifyLetter"
        />

    </div>
</template>



<script>

import Gibbet from './Gibbet';
import Word from './Word';
import KeyBoard from './KeyBoard';

export default{
    name: 'GameItem',
    props:{
        errors: Number,
        word: String,
        tip: String,
        verifyLetter: Function,
        step: String,
        letters: Array
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
        KeyBoard
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
