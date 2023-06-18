<template>
   <div>
    <div v-bind:key="i.id" v-for="i in list">
        <TodoItems v-bind:items="i" v-on:del-todo="$emit('del-todo',i.id) "/>
          </div>
</div>
</template>


<script>
import TodoItems from './TodoItems.vue'
export default {
    name: 'TodosList',
    components:{
        TodoItems
    },
    props: ["list"]
    
}
</script>



<style scoped>

</style>
