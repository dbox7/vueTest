<template>
  <div 
    class="dialog" 
    v-if="visible"
    @click="closeModal"
  >
      <div class="dialog__container" @click.stop>
        <slot></slot>
      </div>
  </div>
</template>

<script>
export default {
  props: {
    visible: {
      type: Boolean,
      default() {
        return false;
      }
    },
  },
  methods: {
    closeModal() {
      this.$emit('update:visible', false)
    }
  }
}
</script>

<style>
  .dialog {
    position: fixed;
    display: flex;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    z-index: 10;
    background: rgba(0, 0, 0, 0.5);
  }

  .dialog__container {
    width: 100%;
    max-width: 500px;
    margin: auto;
  }
</style>