<template>
    <div class="form">
        <div class="form-title">{{title}}</div>

        <input type="text" class="form-input" v-model="inputValue">

        <button 
            :disable="inputValue.length === 0"
            v-on:click="onSubmit"
            >{{buttonTitle}}</button>

         <TextInfoComponent 
            :textError="textError"
            :msgError="msgError"
         />
    </div>    
</template>

<script>
import TextInfoComponent from './TextInfoComponent.vue';


export default {
    name: 'FormComponent',
    props: {
        title: String,
        buttonTitle: String,
        action: Function,
        textError: String,
        msgError: Boolean
    },
    data(){
        return {
            inputValue: ''
        }
    },
    methods:{
        onSubmit: function(){
            this.action(this.inputValue);
            this.inputValue = '';
        }
    },
    components: {
        TextInfoComponent
    }
}
</script>

<style scoped>

    .form{
        display: flex;
        flex-direction: column;
        align-items: center;
        align-content: center;
        justify-content: center;
        margin-top: 20px;
    }

    .form-input{
        padding: 10px 5px;
        border: 0;
        border-radius: 5px;
        margin: 10px 0px;
        text-align: center;
        color: var(--color-text-dark);
        font-size: 16px;
    }

</style>


