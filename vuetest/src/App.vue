<template>
  <h1>List of something</h1>
  <hr>
  <list-items :items="items"/>
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
    margin: 0;
    font-family: Roboto;
  }

  h3 {
    margin: 0;
  }

  h1 {
    text-align: center;
    margin: 15px;
    text-transform: uppercase;
  }
</style>