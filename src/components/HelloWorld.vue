



<script setup>
import {ref,reactive} from 'vue'
// const form=ref({
//     name:""
// })
 let products=reactive([
    {name:"pizza",src:"https://upload.wikimedia.org/wikipedia/commons/9/91/Pizza-3007395.jpg"},
    {name:"burger",src:"https://static.toiimg.com/thumb/83565509.cms?width=1200&height=900"}
]);
const selectedProducts=reactive([]);
const inputText=ref('');
const submittedText=ref('');
// const submitted=ref(false);


const submitForm=(event)=>{
    event.preventDefault(); 
     console.log(selectedProducts);
submittedText.value=inputText.value;
for(let prod of products){
    if(prod.name===submittedText.value){
        selectedProducts.push(prod);
        console.log(selectedProducts);
    }
    products=[]
}
// const nameInput = event.target.elements.name;
// form.value.name=nameInput.value;
// submitted.value=true;
// console.log(form.name);
//    console.log(nameInput.value);
}

</script>

<template>
<div id="form">
<form> 
<label for="inputText">Name</label>
<input type="text" name="name" v-model="inputText">
<button @click="submitForm">submit</button>
</form>
</div>

<!-- <div v-if="submittedText">
  <h1>{{submittedText}} </h1>
  <!-- <h1>{{submitted}}</h1> -->
<!-- </div>  -->

<div id="list-items" v-if="products!==[]">
        <div id="item" v-for="prod in selectedProducts">
        <h1>{{prod.name}}</h1>
            <img v-bind:src="prod.src">
        </div>
</div>
<div id="list-items" v-if="selectedProducts">
        <div id="item" v-for="prod in products">
        <h1>{{prod.name}}</h1>
            <img v-bind:src="prod.src">
        </div>
</div>


</template> 

<style scoped>
#form{
    /* align-content:top; */
    position:absolute;
    top:10%;
    left:20%;
}
#list-items{
    margin:30px 20% 30px;
    /* border:2px solid black; */
    display:grid;
    grid-template-columns:repeat(autofill,minmax(200px,1fr));
    grid-gap:20px;

}
#item{
    /* border:2px solid black; */
}
img{
    height:200px;
    width:200px;
}
</style>
