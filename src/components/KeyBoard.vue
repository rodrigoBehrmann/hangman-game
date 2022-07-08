<template>
    <div class="keyboard">
        
        <button 
            class="keyboard-button" 
            v-for="(letter, key) in 'abcdefghijklmnopqrstuvwxyz'"
            :key="key"
            :disabled="verifyLetter(letter)"
            v-on:click="alert(letter)">
            {{letter}}

        </button>
       

    </div>
</template>



<script>


export default{
    name: 'KeyBoardItem',
    props:{
        letters: Array,
        verifyLetter: Function
    },
    data(){
        return{
            
        }
    },
    methods: {
        
    },
    components:{
        
    }
}
</script>


<style>
   
    .keyboard{
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        width: 80%;
        margin-top: 20px;
    }

    .keyboard-button{
        margin: 5px;
    }

</style>
