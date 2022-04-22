<template>
    <div class="word">
        <div class="word-letters">

            <div class="word-letter" v-for="(letter, index) in word" :key="index" >
                {{ (verifyLetter(letter) || stage === 'enforcado' ) ? letter : '' }}
            </div>

        </div>

        <div class="word-tip">{{ wordTip }}</div>
    </div>    
</template>

<script>


export default {
    name: 'WordComponent',
    props: {
        word: String,
        wordTip: String,
        verifyLetter: Function,
        stage: String
    }    
}
</script>

<style scoped>

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
       width: 30px;
       height: 30px;
       margin: 0px 5px;
       border-bottom: 1px solid var(--color-text-light);
       display: flex;
       justify-content: center;
       align-items: center;
   }
   
</style>


