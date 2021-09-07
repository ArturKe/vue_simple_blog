<template>
    <input type="date" v-model="modelValue" @input="updateInput" >
  
</template>

<script>
export default {
   
    props:{
        modelValue: [String,Date]

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