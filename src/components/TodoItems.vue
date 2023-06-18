<template>
    <div class="todo-item" v-bind:class="{'is-complete': items.completed }"> 
      <p>
        <input type="checkbox" v-on:change="triggercomplete">
        
        {{items.title}}
        
        <button  v-on:click="$emit('del-todo',items.id)" class="del">x</button>
        </p>
    </div>
</template>
 
<script>

export default{

    name: "TodoItems",
    props:["items"],
    methods:
    {
        triggercomplete(){
            this.items.completed=!this.items.completed
        }
    }
    
}
</script>

<style scoped>

.todo-item{
    background: white;
    padding:10px;
    border-bottom: 1px white dotted;
}
.is-complete{
    text-decoration: line-through;

}

.del{
    background: red;
    color:white;
    border:none;
    padding:5px 9px;
    border-radius:50%;
    cursor:pointer;
    float:right;
}
</style>
