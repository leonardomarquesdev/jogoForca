<template>
    <div class="endgame">
       <div :class="`end-text ${stage}`">{{endText}}</div>

       <button 
        class="end-button"
        v-on:click="restart"
        >Jogar novamente</button>
    </div>    
</template>

<script>


export default {
    name: 'EndGameComponent',
    props: {
        stage: String,
        endText: String,
        restart: Function
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

  .end-text{
      margin: 20px 0px;
      font-size: 24px;
      font-weight: bold;
  }

  .end-text.enforcado{
      color:var(--color-text-error);
  }

  .end-text.ganhador{
      color:var(--color-text-success);
  }
   
</style>


