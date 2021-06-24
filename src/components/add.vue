<template>
    <form >
    <div class="item" >
        <input type="text" class="text" v-model="title" placeholder="Enter Your Todo">
        <button @click="addTodo" type="submit" class="add">+</button>
    </div>
    </form>
</template>

<script>
export default {
    name:"add",
    methods:{
        addTodo(e){
            e.preventDefault();
            const newTodo = {
                title:this.title,
                completed:false
            }
        //send up to the parent
        this.$emit('add-todo', newTodo);
        document.getElementsByClassName("text").value = "hello";
        }
    }
}
</script>
input
<style scope>
input[type="text"] {
    margin-left: 20px;
  text-align: center;
  border: none;
  border-bottom: solid;
  background: transparent;
  border-color: #364f6b;
  font-size: 2rem;
  font-weight: 200;
  height: 40px;
  width: 80%;
  outline: none;
}
::placeholder {
  color: grey;
  opacity: 1;
}
.add{
  min-height: 50px;
  width: 50px;
  border-radius: 50%;
  border-color: transparent;
  background-color:#364f6b;
  color: #fff;
  font-size: 2rem;
  padding-bottom: 3px;
  border-width: 0;
  margin-left:20px;
  cursor: pointer;
}

</style>