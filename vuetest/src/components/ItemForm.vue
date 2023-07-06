<template>
  <div class="item">
    <h3 class="title">{{item.name}}</h3>
    <span class="value">{{item.value}}</span>
    <button 
      class="button"
      v-on:click="edit">
        Edit
    </button>
  </div>
</template>

<script>
export default {
  props: {
    item: {
      type: Object
    }
  },
  methods: {
    edit: function () {
      this.$emit('edit', this.item)
    }
  }
}
</script>

<style>
  .item {
    display: flex;
    flex-direction: column;
    align-items: center;
  
    padding: 20px;  
    gap: 15px;
    max-width: 200px;

    border: 2px solid blue;
    border-radius: 20px;
  }

  .value {
    display: flex;
    max-width: 150px;
  }

  .button {
    display: flex;
    justify-content: center;
    text-align: center;

    width: 100%;
    margin-top: 10px;
    padding: 10px;

    border: 1px solid blue;
    border-radius: 15px;
    background: transparent;
    cursor: pointer;
    transition: background 0.5s, transform 0.1s;
  }

  .button:hover {
    background: rgba(0, 0, 250, 0.1);
  }

  .button:active {
    transform: scale(0.9);
  }
</style>