<template>
  <div class="container" :class="{'disable-scroll': visible}">
    <c-modal v-model:visible="visible">
      <item-form
        v-model:item="currentItem"
        :editMode=true
        @updateItem="updateItem"
      />
    </c-modal>
    <item-form
      v-for="(item, index) in items"
      :key="'item-' + index"
      :item="item"
      :editMode=false
      @edit="edit"
    />
  </div>
</template>

<script>
import ItemForm from './ItemForm.vue';
import CModal from './UI/CModal.vue';

export default {
  data() {
    return {
      currentItem: {
        type: Object,
      },
      visible: false,
    }
  },
  components: { CModal, ItemForm },
  props: {
    items: {
      type: Array
    }
  },
  methods: {
    edit(item) {
      this.currentItem = item;
      this.visible = true;
    },
    updateItem(value) {
      this.currentItem.value = value
      this.visible = false;
    }
  }
}
</script>

<style>
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;

    gap: 20px;
    width: 100%;
    max-width: 900px;
    margin: auto;
    padding: 15px;
  }

  .disable-scroll {
    overflow-y: hidden;
  }
</style>