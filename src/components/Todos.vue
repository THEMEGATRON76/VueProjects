<template>
  <div class="box">
    <div v-bind:key="todo.id" v-for="todo in todos" >
        <todoItems v-bind:todo="todo" v-on:del-todo="$emit('del-todo',todo.id)"/>
    </div>
    
  </div>
</template>


<script>
import todoItems from './todoItems.vue'

export default {
  name: "Todos",
  props: ["todos"],
  components:{
      todoItems,
      
  }
};
</script>

<style scope>

</style>