<template>
  <label
    class="c-Checkbox"
    tabindex="0"
    @keydown.space.prevent
    @keyup.enter="onTrigger()"
    @keyup.space="onTrigger()"
  >
    <input
      v-model="state"
      aria-hidden="true"
      class="c-Checkbox__input"
      type="checkbox"
      @click="onTrigger()"
    >
    <div class="c-Checkbox__element"></div>
    <span
      v-if="label"
      class="c-Checkbox__label"
    >
      {{ label }}
    </span>
  </label>
</template>
<script>
export default {
  name: 'Checkbox',
  props: {
    label: {
      type: String,
      required: false,
      default: undefined
    }
  },
  data() {
    return {
      state: false,
    }
  },
  methods: {
    onTrigger() {
      this.state = !this.state
      this.$emit('change', this.state)
    }
  }
}
</script>
<style scoped>
.c-Checkbox {
  cursor: pointer;
  position: relative;
  display: flex;
  align-items: center;
  width: -moz-fit-content;
  width: fit-content;
}

.c-Checkbox input {
  display: none;
}

.c-Checkbox__element {
  position: relative;
  display: block;
  width: 24px;
  height: 24px;
  border: 2px solid;
  border-radius: 4px;
  border-color: black;
  transition: 0.150s;
}

.c-Checkbox__input:checked + .c-Checkbox__element {
  background-color: black;
}

.c-Checkbox__element::after {
  content: "";
  display: block;
  position: absolute;
  left: 2px;
  top: -4px;
  width: 8px;
  height: 14px;
  border-width: 0 3px 3px 0;
  border-style: solid;
  border-color: white;
  transform-origin: bottom left;
  transform: rotate(45deg);
  opacity: 0;
}

.c-Checkbox__input:checked + .c-Checkbox__element::after {
  opacity: 1
}

.c-Checkbox__label {
  user-select: none;
  margin-left: 8px;
}
</style>
