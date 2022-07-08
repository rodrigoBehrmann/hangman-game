<template>
    <div class="gibbet">

        <img :src="`https://raw.githubusercontent.com/william-costa/wdev-hangman-game-resources/master/images/hangman/${errors}.svg`">

    </div>
</template>



<script>



export default{
    name: 'GibbetItem',
    props:{
        errors: Number
    },
    data(){
        return{
            
        }
    },
    methods: {
        
    }
}
</script>


<style>
   
    .gibbet img{
        width: 20%;
    }

</style>
