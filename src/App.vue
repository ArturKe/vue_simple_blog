<template>
  <div id="app">
    
    <h2>Simple Blog</h2>

    <FormCreate label="Form for create Post" @create="addPost" />

    <p>Counter:{{ posts.length }} </p>

    <PostsList :posts="posts" @delete="deletePost"/>
    
  </div>
</template>

<script>
import FormCreate from './components/FormCreate.vue'
import PostsList from './components/PostsList.vue'

export default {

  name: 'App',

  components:{
    FormCreate,
    PostsList
  },

  data(){
    return{
      count:1,
      posts:[
        {id:0, title:"VUE", body:"This is post about VUE", type:'blue'},
        {id:1, title:"REACT", body:"This is post about REACT", type:'red'}
      ]
    }
  },

  methods:{

     addPost(post){
      this.posts.push(post)

    },

    deletePost(id){
      this.posts = this.posts.filter(post => post.id !== id)

    }

  }
}
</script>

<style>

  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  @media screen and (max-width: 767px) {
    input, select, textarea {
      font-size: 16px;
    }
  }

</style>
