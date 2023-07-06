<template>
  <div class="container">
    <c-modal/>
    <item-form
      v-for="(item, index) in items"
      :key="'item-' + index"
      :item="item"
    />
  </div>
</template>

<script>
import ItemForm from './ItemForm.vue';
import CModal from './UI/CModal.vue';

export default {
  components: { CModal, ItemForm },
  props: {
    items: {
      type: Array
    }
  },
  methods: {
    edit: function () {
      this.$emit('edit', this.currentItem)
    }
  }
}
</script>

<style>
  .container {
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;

    gap: 20px;
    width: 100%;
    max-width: 900px;
    margin: auto;
  }
</style>