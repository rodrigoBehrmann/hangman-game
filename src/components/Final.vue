<template>
    <div class="final">
        
       <div :class="`final-text ${step}`">
        {{text}}
       </div>

       <button 
       class="final-button"
       v-on:click="playAgain"
       >
        Play Again
       </button>

    </div>
</template>



<script>


export default{
    name: 'FinalItem',
    props:{
        step: String,
        text: String,
        playAgain: Function
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

    .final-text{
        margin: 20px 0px;
        font-size: 24px;
        font-weight: bold;
    }

    .final-text.hanged{
        color: var(--color-text-error);
    }

    .final-text.winner{
        color: var(--color-text-success);
    }

</style>
