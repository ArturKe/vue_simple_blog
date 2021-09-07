<template>
  <div id="app">

    <h2>Form</h2>

    <div  class="bigForm">

        <div v-for="column in columns" :key="column.columnName">

          <div class="bigForm__item">
            <h3>{{column.columnNameRU}}</h3>

            <div class="bigForm__row"  v-for="item in dataInfo" :key="item.id">
              <component v-bind:is="column.widget" :modelValue = "item[column.columnName]" :disabled="column.config.useOnEdit" ></component>
            </div>
          
          </div>

        </div> 
      
    </div>

    
    <h2>Simple Blog</h2>

    <FormCreate label="Posts creation form" @create="addPost" />

    <p>Counter:{{ posts.length }} </p>

    <PostsList :posts="posts" @delete="deletePost"/>
    
  </div>
</template>

<script>
import FormCreate from './components/FormCreate.vue'
import PostsList from './components/PostsList.vue'
import MyInput from './components/widget/MyInput.vue'
import DatePicker from './components/widget/DatePicker.vue'


export default {

  name: 'App',

  components:{
    FormCreate,
    PostsList,
    MyInput,
    DatePicker
  },

  data(){
    return{
      inputVal:'Tratatat',
      count:1,
      posts:[
        {id:0, title:"VUE", body:"This is post about VUE", type:'blue'},
        {id:1, title:"REACT", body:"This is post about REACT", type:'red'}
      ],
      columns: [
        {
          columnName: 'firstName',
          columnNameRU: 'Имя',
          widget: 'MyInput',
          dataType: 'string',
          config: {
              useOnEdit: false
          }
        },

        {
          columnName: 'lastName',
          columnNameRU: 'Фамилия',
          widget: 'MyInput',
          dataType: 'string',
          config: {
              useOnEdit: true
          }
        },

        {
          columnName: 'date',
          columnNameRU: 'Дата рождения',
          widget: 'DatePicker',
          dataType: 'datetime',
          config: {
              useOnEdit: false
          }
        },
    
      ],
      dataInfo:[
        {
        firstName: 'Алексей',
        date: '1995-01-18',
        id: 2010120,
        lastName: 'Зимин'
        },

        {
        firstName: 'Регина',
        date: '1991-04-28',
        id: 2019320,
        lastName: 'Рябина'
        },

        {
        firstName: 'Феликс',
        date: '1887-03-23',
        id: 2023329,
        lastName: 'Юсупов'
        },


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

  .bigForm{
    display: flex;
    border: 2px solid rgb(175, 175, 175);
    border-radius: 5px;
    padding: 10px;
    overflow: auto;
  }

  .bigForm__item{
    min-width: 170px;
    line-height: 0;
    margin-right: 10px;
    display: flex;
    flex-direction: column;

  }

  .bigForm__row{
    margin-top: 10px;

  }

  /* @media (max-width: 500px) {
    .bigForm{
      justify-content: center;
    }
    
  } */

</style>
