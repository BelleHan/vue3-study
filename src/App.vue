<template>
  <div class="name">
    {{ name }}
  </div>
  <button 
    class="btn btn-primary"
    v-on:click="updateName"
  >
    Click
  </button>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const name = ref('Belle Han');

    // const greeting = (name) => {
    //   return 'Hello, ' + name;
    // };

    // const greet = greeting(name);

    const updateName = () => {
      name.value = 'Heesu Han';
      console.log(name);
    };

    return {
      name,
      updateName,
    };
  }
}
</script>

<style>
  .name{
    color: blueviolet;
  }
</style>