<template>
    <div>
        <div  v-for="(post, index) in posts" :key="post.id"> 
            <div :class="'postCard ' + post.type ">

                <div class="postCard__top">
                    <div class="postCard__title">
                        <h3>#{{index}} Title: {{post.title}}</h3>
                        <h4 class="postCard__time">{{new Date(post.id).toLocaleTimeString('it-IT')}}  {{ new Date(post.id).toLocaleDateString() }}</h4>

                    </div>
                    
                    <button @click="deletePost(post.id)">Delete</button>
                </div>

                <div >{{post.body}}</div> 

            </div>
            
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

    .postCard.red{
        background-color: #ffdfef;
    }

    .postCard.violet{
        background-color: #f7d6ff;
    }

    .postCard.blue{
        background-color: #e0e6f3;
    }

    .postCard.green{
        background-color: #dfffea;
    }

    .postCard.white{
        background-color: #ffffff;
    }

    .postCard.ocean{
        background-color: #a8e6f3;
    }

    .postCard.sun{
        background-color: #ffe290;
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

    .postCard__time{
        color: gray;

    }

    .postCard__title{
        display: flex;
        flex-direction: column;
        align-items:flex-start;
        line-height: 0;
        padding-left: 5px;

    }

</style>