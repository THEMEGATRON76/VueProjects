<template>
 <div >
     <div class="items" v-bind:class="{'isComplete':todo.completed}">
               
         <p>
          <input type="checkbox" @change="markCompleted"> 
          
           {{todo.title}}

           <button class="del" @click="$emit('del-todo',todo.id)"><i class="fas fa-trash"></i></button>
         </p>
         
     </div>
 </div>



</template>

<script>
export default {
  name: "todoItems",
  props:["todo"],
  data(){
    return {
    thisTodo: this.todo
    }
  },
  methods:{
    markCompleted(){
      this.thisTodo.completed = !this.thisTodo.completed;
    }
  }
};
</script>


<style scope>
p{
  font-size: 2rem;
  margin-bottom: 0px ;
}

.del{
  background-color: white ;
  color: red;
  margin-top:8px ;
  font-size: 1.3rem;
  margin-right: 5px;
  float: right;
  border: none;
  cursor: pointer;
}
.item {
  min-height: 70px;
  display: flex;
  align-items: center;
  border-bottom: 1px solid #f1f1f1;
}
.isComplete{
    text-decoration: line-through;
    text-decoration-color: #A683E3;
}
input[type="checkbox"] {
  margin: 20px;
  cursor: pointer;
}
</style>