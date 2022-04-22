<template>
    <div class="forca">
        
        <img :src="`https://raw.githubusercontent.com/william-costa/wdev-hangman-game-resources/master/images/hangman/${errors}.svg
`" alt="">


    </div>    
</template>

<script>


export default {
    name: 'ForcaComponent',
    props: {
        errors: Number
    },
    data(){
        return {
           
        }
    },
    methods:{
       
    }
}
</script>

<style scoped>

    .forca img{
        height: 100px;
    }
   
</style>


