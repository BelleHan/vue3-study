<template>
  <div :class="nameClass">
    {{ name }}
  </div>
  <input v-bind:type="type" v-bind:value="name">
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
    const name = ref('Belle');
    const type = ref('number');
    const nameClass = ref('');

    const updateName = () => {
      name.value = 'Heesu';
      type.value = 'text';
      nameClass.value = 'name';
    };

    return {
      name,
      updateName,
      type,
      nameClass,
    };
  }
}
</script>

<style>
  .name{
    color: blueviolet;
  }
</style>