<template>
    <h1
      class="font-semibold text-center mt-10 text-sky-600 text-3xl transition duration-500 hover:scale-125 cursor-pointer"
    >
      Fruits List
    </h1>
  

    <div class="text-center mt-10">
      <input
        v-model="entertask"
        type="text"
        placeholder="Enter a fruit name"
        class="border-2 border-black p-2 rounded-lg w-2/4 shadow-lg"
        @keyup.enter="addtask"
      />
      <button
        @click="addtask"
        class="p-2 bg-yellow-500 rounded-lg mx-2 text-white transition duration-300 hover:scale-110 shadow-lg"
      >
        Add Fruit
      </button>
    </div>

    <ul class="mt-5">
      <li
        class="border-2 p-2 rounded-lg shadow-lg w-2/4 m-auto flex justify-between items-center"
        v-for="(fruit, index) in fruitlist"
        :key="index"
      >
        <span>{{ fruit }}</span>
        <button
          @click="removeTask(index)"
          class="p-1 bg-red-500 text-white rounded-lg transition duration-300 hover:scale-110"
        >
          Remove
        </button>
      </li>
    </ul>
  </template>
  
  <script setup>
  import { ref } from "vue";
  const entertask = ref(""); 
  const fruitlist = ref([]); 
  
  const addtask = () => {
    if (entertask.value.trim()) {
      fruitlist.value.push(entertask.value); 
      entertask.value = ""; 
    }
  };
  

  const removeTask = (index) => {
    fruitlist.value.splice(index, 1); 
  };
  </script>
  