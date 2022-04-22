<template>
    <div class="keyboard">
        <button 
            class="keyboard-button" 
            v-for="(letter, index) in 'abcdefghijklmnopqrstuvwxyz'" 
            :key="index"
            :disable="verifyLetter(letter)"
            v-on:click="playLetter(letter)">
            {{ letter }}
        </button>
    </div>    
</template>

<script>


export default {
    name: 'KeyboardComponent',
    props: {
        letters: Array,
        verifyLetter: Function,
        playLetter: Function
    }   
}
</script>

<style scoped>

  .keyboard{
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      max-width: 85%;      
      margin-top: 15px;
  }

  .keyboard-button{
      margin: 5px;
      text-transform: uppercase;
  }
   
</style>


