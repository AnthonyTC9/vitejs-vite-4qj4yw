<script setup>
  import {ref, computed} from 'vue';
    const name = "Vue 3";
    /*const styleColor = "color: red;";
    const active = true;
    const arrayFrutas = ["🍎", "🍌", "🍉", "🍓", "🍒"];
        const arrayFrutax = [
        {
            name: "Manzana",
            price: "$1.00",
            description: "Una manzana",
        },
        {
            name: "Pera",
            price: "$2.00",
            description: "Una pera",
        },
        {
            name: "Naranja",
            price: "$3.00",
            description: "Una naranja",
        },
    ];

        const frutaz = {
        name: "Naranja",
        price: "$3.00",
        description: "Una naranja",
    };
    const arrayFrutxs = [
      {
          name: "Manzana",
          price: "$1.00",
          description: "Una manzana",
          stock: 0,
      },
      {
          name: "Pera",
          price: "$2.00",
          description: "Una pera",
          stock: 10,
      },
      {
          name: "Naranja",
          price: "$3.00",
          description: "Una naranja",
          stock: 20,
      },
    ];

    const handleClick = () => {
    console.log("me diste cick");
    };
    */
    
    const counter = ref(0);
     const arrayFavoritos = ref([]);

    const increment = () => {
      counter.value ++;
    };
    const decrement = () => {
      counter.value --;
    };
    const reset = () => {
      counter.value  = 0;
    };
    const add = () => {
      arrayFavoritos.value.push(counter.value);
    };

    const bloquearBtnAdd = computed(() => {
      const numSearch = arrayFavoritos.value.find(num => num === counter.value);
      console.log(numSearch);
      if(numSearch === 0) return true;
      return numSearch ? true : false;
      //return numSearch || numSearch === 0;
    });

    const classCounter = computed(() => {
      if(counter.value === 0){
        return 'zero';
      }
      if(counter.value > 0){
        return 'positive';
      }
      if(counter.value < 0){
        return 'negative';
      }
    });

   

</script>

<template>

  <div class="container text-center mt-3">
        <h1>Hola {{ name.toUpperCase() }}!</h1>

        <h2 :class="classCounter"> {{counter}} </h2>
        <div class="btn-group">
          <button @click="increment" class="btn btn-success">Aumentar</button>
          <button @click="decrement" class="btn btn-danger">Disminuir</button>
          <button @click="reset" class="btn btn-secondary">Regresar a 0</button>
          <button @click="add" :disabled="bloquearBtnAdd" class="btn btn-primary">Agregar</button>
        </div>
        <ul class="list-group mt-4">
          <li v-for="(num,index) in arrayFavoritos" :key="index" class="list-group-item">
            {{num}}
          </li>
        </ul>
    </div>

<!--
    <button v-on:click.right.prevent="handleClick('Mensaje desde botón')">Click Derecho</button>
    <button @click.left="handleClick('Mensaje desde botón')">Click Izquierdo</button>
    <button @click.middle="handleClick('Mensaje desde botón')">Click Medio</button>



    <h2 v-bind:style="styleColor">Hola {{ name }}</h2>
    <h2 v-if="active === true">Estoy en true</h2>
    <h2 v-else-if="active === false">Estoy en false</h2>
    <h2 v-else>Estoy indeciso</h2>
    <h2 v-show="active">Estoy en true</h2>
        <ul>
        <li v-for="(fruta, index) in arrayFrutas" :key="index">
            {{ fruta }}
        </li>
    </ul>

        <ul>
        <li v-for="fruta in arrayFrutax" :key="name">
            {{ fruta.name }} - {{ fruta.price }} - {{ fruta.description }}
        </li>
    </ul>
        <ul>
        <li v-for="(value, propiedad) in frutaz">
            {{ propiedad }} : {{ value }}
        </li>
    </ul>

  <ul>
      <template v-for="item in arrayFrutxs" :key="item.name">
          <li v-if="item.stock > 0">{{item.name}} - {{item.price}}
          </li>
      </template>
  </ul>
  -->
</template>

<style scoped>

.positive{
  color: green;
}

.negative{
  color: red;
}

.zero {
  color: peru;
}

</style>