<template>
    <form class="form" @submit.prevent>
        <h3>{{ label }}</h3>
        <input :class="warnTitle ? 'warn' : ''" v-bind:value = "post.title" @input = "post.title = $event.target.value" placeholder="Title" >
        <input v-bind:value = "post.body" @input = "post.body = $event.target.value" placeholder="Text">
        <button @click="createPost">Publish</button>
    </form>
</template>

<script>
export default {

    name:'FormCreate',
    data(){
        return{
            colors:[
                'red',
                'sun',
                'blue',
                'violet',
                'green',
                'white',
                'ocean'
            ],

            post:{
                title:'',
                body:''
            },
            warnTitle: false,
            classId:"warn"
            
        }
    },

    methods:{
        createPost(){
            let randomIndex = Math.floor(Math.random()*this.colors.length)
           
            this.post.id = Date.now()
            this.post.type = this.colors[randomIndex]
            console.log(randomIndex)
    
            this.$emit('create', this.post)
            this.post = {
            title:'',
            body:'',
            }
            this.warnTitle = false

        }

    },

    props:{
        label: String
    }

}
</script>

<style scoped>

    .form{
        margin: 0 auto;
        max-width: 300px;
        display: flex;
        flex-direction: column;
    }

    .form button{
    margin-top: 10px ;
    background-color: none;
    height: 45px;
    border-radius: 10px;
    cursor: pointer;
    font-size: 20px;
    }

    .form input{
    margin-top: 10px;
    height: 25px;
    border-radius: 5px ;
    border: 2px solid grey
    }

    .form input.warn{
    margin-top: 10px;
    height: 25px;
    border-radius: 5px ;
    border: 3px solid red;
    background-color:rgb(248, 231, 231)
    }



</style>
