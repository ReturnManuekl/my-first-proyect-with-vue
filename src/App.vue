<script setup>
  import {ref, computed} from 'vue';

  const name = "Vue dinamico";

  const favorites = ref([]);

  const counter = ref(0);

  const increment = () => counter.value ++;

  const decrement = () => counter.value --;

  const reset = () => counter.value = 0;

  const add = () => {
    favorites.value.push(counter.value);
  };

  const classCounter = computed(() => {
    if (counter.value === 0) {
      return 'zero'
    }
    if (counter.value > 0) {
      return 'positive'
    }
    if (counter.value < 0) {
      return 'negative'
    }
  });

 

  const desactivar = computed(() => {
    if (favorites.value.includes(counter.value)) {
      return 'true';
    }
  });


</script>

<template>
  <div class="container text-center mt-3">
    <h1>Hola {{ name.toUpperCase() }}</h1>
    <h2 :class="classCounter">{{ counter }}</h2>
    <div class="btn-group">
      <button @click="increment" class="btn btn-success">Increment</button>
      <button @click="decrement" class="btn btn-danger">Decrement</button>
      <button @click="reset" class="btn btn-secondary">Reset</button>
      <button :disabled="desactivar" @click="add" class="btn btn-primary">Add</button>
    </div>
    <ul class="list-group mt-4">
      <li v-for="(number, index) in favorites" :key="index" class="list-group-item">
        {{ number }}
      </li>
    </ul>
  </div>
  
</template>

<style>
  h1 {
    color: red;
  }
  .positive {
    color: green;
  }
  .negative {
    color: red;
  }
  .zero {
    color: peru;
  }
</style>