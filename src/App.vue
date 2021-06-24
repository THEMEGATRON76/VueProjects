<template>
  <heading />
  <Todos v-bind:todos="todos" v-on:del-todo="deletes"  /> 
  
  <add class="boxs" v-on:add-todo="addNew"/>
  
</template>

<script>
import Todos from "./components/Todos.vue"
import heading from "./components/heading.vue"
import add from "./components/add.vue"
import axios from 'axios'
export default {
  name: 'App',
  components: {
    Todos,
    heading,
    add
  },
  data (){
    return{
      todos:[]
    }
  },
  mounted:function(){
    this.created();
  },
  methods:{
    deletes(id) {
      const iid = id;
      axios.delete("https://jsonplaceholder.typicode.com/todos/"+iid)
      .then(this.todos = this.todos.filter(todo => todo.id !== id))
      .catch(err => console.log(err));
    },
    addNew(newTodo){
      //this.todos = [...this.todos, newTodo];
      //my way
      const {title,completed}= newTodo;
      axios.post("https://jsonplaceholder.typicode.com/todos",{
        title,
        completed
      })
      .then(ress => this.todos = [...this.todos, ress.data])
      .catch(err => console.log(err));
     
    },
    created(){
      axios.get("https://jsonplaceholder.typicode.com/todos?_limit=5")
      .then(res => this.todos = res.data)
      .catch(err => console.log(err));

    }
  }
}
</script>

<style>
html {
  background-color: #E4E9FD;
  background-image: -webkit-linear-gradient(65deg, #11999e 50%, #e4f9f5 50%);
  min-height: 1000px;
  font-family: 'Varela Round', sans-serif;
}
.box {
  max-width: 600px;
  margin: 50px auto 0px auto;
  background: white;
  border-radius: 5px;
  border-bottom-left-radius:0 ;
  border-bottom-right-radius: 0;
  box-shadow: 5px 5px 15px -5px rgba(0, 0, 0, 0.3);
}
.boxs{
  max-width: 600px;
  margin: 0px auto 0px auto;
  background: white;
  border-bottom-left-radius:5px;
  border-bottom-right-radius:5px;
  box-shadow: 5px 5px 15px -5px rgba(0, 0, 0, 0.3);
}
</style>
