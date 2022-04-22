<template>
  <div id="app">
    <h1>Jogo da Forca WDEV</h1>

    <section v-if="tela==='inicio'" id="inicio">
      <FormComponent v-if="etapa === 'palavra'"
        title="Defina a palavra"
        buttonTitle="Próximo"
        :action="setPalavra"
      />

      <FormComponent v-if="etapa === 'dica'"
        title="Defina a dica"
        buttonTitle="Iniciar jogo :)"
        :action="setDica"
      />
    </section>

    <section v-if="tela==='jogo'" id="jogo">
      <GameComponent 
        :errors="erros" 
        :word="palavra"
        :wordTip="dica"
        :verifyLetter="verificarLetra"
        :stage="etapa"
        :letters="letras"
        :playLetter="jogarLetra"
        :restart="jogarNovamente"
      />
    </section>
  </div>
</template>

<script>
import './css/global.css';
import FormComponent from './components/FormComponent.vue'
import GameComponent from './components/GameComponent.vue'

export default {
  name: 'App',
  data(){
    return {
      tela: 'inicio',
      etapa: 'palavra',
      palavra: '',
      dica: '',
      erros: 0,
      letras: []
    }
  },
  components: {
    FormComponent,
    GameComponent
  },
  methods:{
    setPalavra: function(palavra){
      this.palavra = palavra;
      this.etapa = 'dica';
    },
    setDica: function(dica){
      this.dica = dica;
      this.etapa = 'jogo';
      this.tela = 'jogo';
    },
    verificarLetra: function(letra){
      return this.letras.find(item => item.toLowerCase() === letra.toLowerCase());
    },
    jogarLetra: function(letra){
      //Adiciona letra jogada
      this.letras.push(letra);
      //Validar erro
      this.verificarErros(letra);
    },
    verificarErros: function(letra){
      //acerto
      if(this.palavra.toLowerCase().indexOf(letra.toLowerCase()) >= 0){
        return this.verificarAcertos();
      }

      //Erros
      this.erros++;
      
      //Enforcado
      if(this.erros === 6)
        this.etapa = 'enforcado'
    },
    verificarAcertos: function(){
      let letrasUnicas = [...new Set(this.palavra.split(''))];
      if(letrasUnicas.length === (this.letras.length - this.erros)){
        this.etapa = 'ganhador';
      }
    },
    jogarNovamente: function(){
      this.palavra = '';
      this.dica=  '';
      this.erros = 0;
      this.letras = [];
      this.tela = 'inicio';
      this.etapa = 'palavra';
    }
  }
}
</script>

<style>
  #app{
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
</style>
