<template>
  <dialog class="dialog" v-if="visible">
    <div class="dialog__container">
      <span>{{item.name}}</span>
      <input placeholder="item.value"/>
    </div>
  </dialog>
</template>

<script>
export default {
  name: 'CModal',
  props: {
    visible: {
      type: Boolean,
      default: false
    },
    item: {
      type: Object
    }
  }
}
</script>

<style>

</style>