<template>
  <button type="button">{{ label }}</button> 
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