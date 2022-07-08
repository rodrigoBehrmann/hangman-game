<template>
    <div class="word">

       <div class="word-letters">

            <div class="word-letter" v-for="(letter,key) in word" :key="key">
                {{(verifyLetter(letter) || step === 'hanged') ? letter : '' }}
            </div>

        </div>

        <div class="word-tip">
            {{tip}}
        </div>

    </div>
</template>



<script>


export default{
    name: 'WordItem',
    props:{
        word: String,
        tip : String,
        verifyLetter: Function,
        step: String
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
   
    .word{
        text-transform: uppercase;
        display: flex;
        flex-direction: column;
        text-align: center;
        align-items: center;
    }

    .word-letters{
        display: flex;
        margin-bottom: 20px;
    }

    .word-letter{
        height: 30px;
        width: 30px;
        margin: 0px 5px;
        border-bottom: 1px solid var(--color-text-light);
        display: flex;
        justify-content: center;
        align-items: center;
    }

</style>
