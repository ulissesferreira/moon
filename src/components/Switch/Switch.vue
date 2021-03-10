<template>
  <label
    class="c-Switch"
    tabindex="0"
    @keydown.space.prevent
    @keyup.enter="onTrigger()"
    @keyup.space="onTrigger()"
  >
    <input
      v-model="state"
      aria-hidden="true"
      class="c-Switch__input"
      type="checkbox"
      @click="onTrigger()"
    >
    <div class="c-Switch__slider" />
    <span
      v-if="label"
      class="c-Switch__label"
    >
      {{ label }}
    </span>
  </label>
</template>
<script>
export default {
  name: 'Switch',
  props: {
    modelValue: {
      type: Boolean,
      required: false,
      default: false,
    },
    label: {
      type: String,
      required: false,
      default: undefined
    }
  },
  emits: [
    'update:modelValue'
  ],
  data() {
    return {
      state: this.modelValue,
    }
  },
  methods: {
    onTrigger() {
      this.state = !this.state
      this.$emit('update:modelValue', this.state)
    }
  }
}
</script>
<style scoped>
.c-Switch {
  cursor: pointer;
  position: relative;
  display: flex;
  align-items: center;
  width: -moz-fit-content;
  width: fit-content;
}

.c-Switch input {
  display: none;
}

.c-Switch__slider {
  position: relative;
  display: block;
  width: 48px;
  height: 24px;
  border-radius: 24px;
  background-color: #ccc;
  transition: 0.150s;
}

.c-Switch__slider:before {
  border-radius: 24px;
  position: absolute;
  content: "";
  height: 20px;
  width: 20px;
  left: 2px;
  bottom: 2px;
  background-color: white;
  transition: 0.150s;
}

.c-Switch__input:checked + .c-Switch__slider {
  background-color: #101010;
}

.c-Switch__input:focus + .c-Switch__slider {
  box-shadow: 0 0 1px #101010;
}

.c-Switch__input:checked + .c-Switch__slider:before {
  transform: translateX(24px);
}

.c-Switch__label {
  user-select: none;
  margin-left: 8px;
}
</style>
