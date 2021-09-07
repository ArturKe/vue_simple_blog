<template>
    <input type="text" v-model="modelValue" @input="updateInput" >
  
</template>

<script>
export default {
   
    props:{
        modelValue:[String,Number]

    },

    methods:{
        updateInput(event){
            console.log(event.target.value)
            this.$emit('input', this.modelValue)

        }
    }

}
</script>

<style>

</style>