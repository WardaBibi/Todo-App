<template>
    <div>
      <form @submit="addTodoItems">
          <input type="text" v-model="title" name="tiitle" placeholder="Add todo...">
          <input type="submit" value="Submit" class="btn">
      </form>  
    </div>
</template>



<script>
//import uuid from 'uuid'
export default {

   name:"AddTodo",
   data(){
    return{
        title:''
    }
   },
   methods:
   {
       addTodoItems(e){
        e.preventDefault();
        const newTodo={
        
            title :  this.title,
            completed: false
        }
       
       this.$emit('addedTodo',newTodo);
       this.title='';
    }
   }

}
</script>


<style scoped>
    form {
        display:flex;

    }
    input[type="text"]{
        flex:10;
        padding:5px;
    }
    input[type="submit"]{
        flex:2;
    }
</style>