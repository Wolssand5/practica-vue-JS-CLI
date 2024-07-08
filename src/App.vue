<script setup>
import { ref, computed} from 'vue';
const navigacion = "soy un const navigacion";
const color = "color:blue";
const arraycolor = ["blue", "green", "aqua", "black"];
const activo = true;
const frutas = ["piña", "mango", "banana", "manzana"];
const arrayfrutas = 
  {
    name: "manzana",
    precio: "$5.00",
    descrip:"fruta",
    stock :10,
  }
  ;

const variasFrutas = [
  {
    name: "manzana",
    precio: "$5.00",
    description: "una manzana",
    stock: 0
  },
  {
    name: "mango",
    precio: "$8.00",
    description: "un manga",
    stock: 45,
  },
  {
    name: "piña",
    precio: "$10.00",
    description: "una piña",
    stock: 14,
  },
  {
    name: "naranja",
    precio: "$15.00",
    description: "una naranja",
    stock: 24
  },
    {
    name: "limon",
    precio: "$15.00",
    description: "una naranja",
    stock: 24
  }
    
  ]
//metodo -methods

const manoClick = (message) => {
  
  console.log("message")
}
//increment
const count = ref(0);
const increment = () => count.value++;
 
const decrement = () => count.value--;
 
const reiniciar = () => count.value = 0;
  
const classCount = computed(() => {
  if (count.value === 0) {
    return 'zero'
  } else if (count.value > 0) {
   return 'positif '
  } else {
    return 'negatif'
  }
});

const arrayFavorito = ref([]);

const add = () => {
  arrayFavorito.value.push(count.value)
}
const blockNumRepetido = computed( ()=> {
  const numero = arrayFavorito.value.find((num) => num == count.value);
  if (numero == 0) return true;
return numero ? true : false;
  // return numero || numero === 0;  // 
}) 
</script>



<template>
  <div class="container text-center mt-3 pt-6">

  <p :class="classCount" >{{count}}</p>

<div class="btn-group col-6 mx-auto ">
  <button class="btn btn-success btn-sm " @click=" increment ">Aumentar</button>
<button class="btn btn-danger btn-sm" @click=" decrement ">Decrementar</button>
<button class="btn btn-warning btn-sm" @click=" reiniciar ">reset</button>
<button class="btn btn-primary btn-sm" :disabled="blockNumRepetido " @click="add">add</button>

</div>
<div class="list mt-3 mb-3">
<ul class="list-group list-group " v-for="(num,index) of arrayFavorito" :key="index" >
  <li class="list-group-item mt-1">
        <span class="badge text-bg-primary rounded-pill mx-3">{{index}}</span>
        Mi numero es {{num}}
  </li>
</ul>
</div>

  <h1>hola {{ navigacion.toUpperCase() }}</h1>
  <p :style="color">soy el color blue{{ arraycolor }}</p>
  <p :style="`color:${arraycolor[1]}`">soy el color array de color</p>

  <h4>{{ activo ? "estoy active" : "no estoy" }}</h4>
  <p v-if="activo">estoy active</p>
  <p v-if="!activo">estoy inactive</p>
 
  <h2 v-show="activo">estoy show</h2>

  <ul>
    <li v-for="(fruit, index) of frutas" :key="index"> <!---in y of es igual--->
      {{ index }}-{{ fruit }}
    </li>
  </ul>

  <br/>
  <ul>
    <li v-for="(value ,propiedad, index) in arrayfrutas" :key="index">
    {{index}}-  {{propiedad}} :  {{value}}

    </li>
  </ul>
 <br/>

<table class="table table-primary">
  <thead>
    <tr>
     
      <th scope="col" >Productos</th>
      <th >Precio</th>
       <th>Description</th>
      <th>Cantidad</th>
      </tr>
    </thead>
    <tbody v-for="item of variasFrutas" :key="item.stock" class="table table-striped">
      <tr>
        <td v-if="item.stock > 0">{{ item.name }}</td>
         <td v-if="item.stock > 0">{{ item.precio }}</td>
          <td v-if="item.stock > 0">{{ item.description }}</td>
           <td v-if="item.stock > 0">{{ item.stock}}</td>
        </tr>
      </tbody>
    </table>
    <br>
  
   <bottom @click ="manoClick(message)" >Clickme</bottom>
</div>
</template>


<style>

h1 {
  color: rgb(22, 248, 14);
}
.positif{
  color:rgb(21, 255, 0)
}
.negatif{
  color:red
}.zero{
  color: gold;
}
</style>
