<template>
  <button
    class="c-Button"
    type="button"
  >
    <span class="c-Button__label">{{ label }}</span>
  </button>
</template>
<script>
export default {
  name: 'Button',
  props: {
    label: {
      type: String,
      required: false,
      default: undefined,
    }
  },
}
</script>
<style scoped>
.c-Button {
  display: flex;
}
</style>
