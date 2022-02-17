<template>
  <button type="button" class="search" @click="$emit('search')">Search<ion-icon name="arrow-forward-outline"></ion-icon></button>
</template>

<script>
export default {
  name: 'SearchButton',
}
</script>

<style lang="scss" scoped>
  button {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-left: 20px;
    width: 100px;
    border: none;
    border-radius: 10px;
    background: rgba(238, 238, 238, 0.562);
    cursor: pointer;
  
    ion-icon {
      margin-left: 5px;
    }
  }
</style>