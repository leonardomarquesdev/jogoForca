<template>
    <div 
      v-if="msgError === true"
      class=input-error>{{ textError }}</div>    
</template>

<script>
export default {
    name: 'TextInfoComponent',
    props: {
        textError: String,
        msgError: Boolean
    }
}
</script>

<style scoped>
    .input-error{
        margin-top: 20px;
        color:  rgb(218, 182, 26);
    }
</style>