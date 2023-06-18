<template>
  <div id="app">
    <Header/>
    <AddTodo v-on:addedTodo="addTodo"/>
   <TodosList v-bind:list="Todos" v-on:del-todo="deleteTodo" />
  </div>

</template>

<script>
import AddTodo from './components/AddTodo';
import TodosList from './components/TodosList';
import Header from './components/layouts/Header';
import axios from 'axios';
export default {
  name: 'App',
  components: {
   TodosList,
   Header,
   AddTodo
  },
  data(){
    return{
      Todos:[]
  }
},
methods:{
  deleteTodo(id){
    axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
    .then(res=> this.Todos = this.Todos.filter(iterator => iterator.id !== id))
    .catch(err => console.log(err))
    
  },
  addTodo(newtodo){

    const {title,completed} = newtodo;

    axios.post('https://jsonplaceholder.typicode.com/todos',{
      title,completed
    })
    .then(res => this.Todos=[...this.Todos, res.data])
    .catch(err =>console.log(err))

  }
},
created(){
     axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
     .then(res => this.Todos = res.data)
     .catch(err => console.log(err));
}
}
</script>

<style>
* {
  box-sizing : border-box;
  margin: 0;
  padding:0;
}
body{
  font-family:Arial, Helvetica, sans-serif;
  line-height: 1.4;
 
}
.btn{
  display:inline-block;
  border:none;
  background: grey;
  color:white;
  padding:7px 20px;
  cursor:pointer;
}

.btn:hover{
  background:lightslategray;
}
</style>
