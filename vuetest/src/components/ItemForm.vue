<template>
  <!-- EditMode on -->
  <div class="item" v-if="editMode">
    <h4 class="desc">Edit information</h4> 
    <h3>{{item.name}}</h3>
    <input 
      :value="item.value" 
      @input="newValue = $event.target.value"
    />
    <button 
      class="button"
      @click="update">
        Save
    </button>
  </div>
  <!-- EditMode off -->
  <div class="item" v-else>
    <h3 class="title">{{item.name}}</h3>
    <span class="value">{{item.value}}</span>
    <button 
      class="button"
      @click="edit">
        Edit
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newValue: ''
    }
  },
  props: {
    item: {
      type: Object
    },
    editMode: {
      type: Boolean,
      default() {
        return false
      }
    }
  },
  methods: {
    edit() {
      this.$emit('edit', this.item)
    },
    update() {
      this.newValue = this.newValue === '' ? this.item.value : this.newValue;
      this.$emit("updateItem", this.newValue)
    }
  }
}
</script>

<style>
  .item {
    display: flex;
    flex-direction: column;
    align-items: left;
  
    padding: 20px;  
    gap: 15px;
    width: 100%;
    max-width: 500px;

    background: white;
    border: 2px solid blue;
    border-radius: 20px;
  }

  .desc {
    text-align: center;
    font-weight: 400;
  }

  .value {
    display: flex;
    max-width: 450px;
  }

  .button {
    display: flex;
    justify-content: center;
    align-self: center;
    text-align: center;

    width: 50%;
    margin-top: 10px;
    padding: 10px;

    border: 1px solid blue;
    border-radius: 15px;
    background: transparent;
    cursor: pointer;
    transition: background 0.5s, transform 0.1s;
    font-size: 16px;
  }

  .button:hover {
    background: rgba(0, 0, 250, 0.1);
  }

  .button:active {
    transform: scale(0.95);
  }
</style>