<template>
  <p>Reaction Time is {{ score }}</p> 
  <p>Reaction Time is {{ message }}</p> 
</template>

<script>
export default {

    props: ['score'],
    data(){
        return {
            message : null,
        }
    },
    mounted(){
        if(this.score < 500){
            this.message = "You are Fast"
        }else{
            this.message = "You are Slow as hell"
        }
    }
}
</script>

<style>

</style>