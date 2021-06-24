<template>
    <h1>Today is {{dates}}</h1>
    <h1 class="secondHeading">Your to-do List</h1>
</template>

<script>
export default {
    name:"heading",
    data (){
        return{
            dates:""
        }
    },
     mounted:function(){
        this.findDate() 
  },
    methods:{
        findDate(){
            let options = {
                weekday: "long",
                day: "numeric",
                month: "long"
                            }
            let d = new Date();
           this.dates = d.toLocaleString("en-US", options);

        }
    }
}
</script>

<style scope>
h1{
    color: #364f6b;
    text-align: center;
    font-size: 3.5rem;
}
.secondHeading{
    margin-top: 80px;
}


</style>