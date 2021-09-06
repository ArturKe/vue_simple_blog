<template>
    <div>
        <div class="postCard"  v-for="post in posts" :key="post.id"> 
            <div class="postCard__top">
                <h3>Title: {{post.title}}</h3>
                <button @click="deletePost(post.id)">Delete</button>
            </div>

            <div >{{post.body}}</div> 
        </div>
    </div>
    
  
</template>

<script>
    export default {
        props:{
            posts: Array
        },

        methods:{
            deletePost(id){
                console.log(id)
                this.$emit('delete', id)
            }
        }

    }
</script>

<style>
    .postCard{
        max-width:800px;
        min-height: 50px;
        border: 1px solid grey;
        border-radius: 5px;
        margin: 0 auto;
        margin-top: 10px;  
        padding: 5px;
        display: flex;
        flex-direction: column;
        align-items: flex-start;
    }


    .postCard__top{
    width: 100% ;
    display: flex;
    justify-content: space-between;
    }

    .postCard button{
        background-color: none;
        height: 45px;
        border-radius: 8px;
        border: 1px solid black;
        cursor: pointer;
        font-size: 16px;
    }

</style>