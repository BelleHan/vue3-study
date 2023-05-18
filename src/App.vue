<template>
  <div class="name">{{ name }}</div>
</template>

<script>
export default {
  setup() {
    const name = 'Belle Han';

    return {
      name
    };
  }
}
</script>

<style>
  .name{
    color: blueviolet;
  }
</style>