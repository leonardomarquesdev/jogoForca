<template>
    <div class="game">
        
        <ForcaComponent 
            :errors="errors"
        />

        <WordComponent 
            :word="word"
            :wordTip="wordTip"
            :verifyLetter="verifyLetter"
            :stage="stage"
        />

        <KeyboardComponent 
            v-if="stage === 'jogo'"
            :letters="letters"
            :verifyLetter="verifyLetter"
            :playLetter="playLetter"
        />

        <EndGameComponent 
            v-if="stage != 'jogo'"
            :stage="stage"
            :endText="stage === 'ganhador' ? 'Acertou, parabéns! :)' : 'Você perdeu :('"
            :restart="restart"
        />

    </div>    
</template>

<script>
import ForcaComponent from './ForcaComponent.vue';
import WordComponent from './WordComponent.vue';
import KeyboardComponent from './KeyboardComponent.vue'
import EndGameComponent from './EndGameComponent.vue';


export default {
    name: 'GameComponent',
    props: {
        errors: Number,
        word: String,
        wordTip: String,
        verifyLetter: Function,
        stage: String,
        letters: Array,
        playLetter: Function,
        restart: Function
    },    
    components:{
        ForcaComponent,
        WordComponent,
        KeyboardComponent,
        EndGameComponent
    }
}
</script>

<style scoped>

    .game{
        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        text-align: center;
    }
   
</style>


