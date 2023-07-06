<template>
  <list-items 
    v-bind:items="items"
    v-bind:callback="edit"
  />
</template>

<script>
import data from './data.json';
import ListItems from './components/ListItems.vue';

export default {
  components: {
    ListItems
  },
  data() {
    return {
      items: data
    }
  }
}
</script>

<style>
  * {
    box-sizing: border-box;
  }

  h3 {
    margin: 0;
  }
</style>