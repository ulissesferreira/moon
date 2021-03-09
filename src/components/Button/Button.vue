<template>
  <button
    class="c-Button"
    type="button"
    :title="title"
    :aria-label="title"
    :disabled="disabled"
    @click="onClick($event)"
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
    },
    title: {
      type: String,
      required: false,
      default: undefined,
    },
    buttonType: {
      type: String,
      required: false,
      default: 'default',
      validator(buttonType) {
        return [
          'default',
          'outlined',
          'text'
        ].includes(buttonType)
      }
    },
    disabled: {
      type: Boolean,
      required: false,
      default: false,
    }
  },
  computed: {
    buttonClassObject() {
      return {
        'is-outlined': this.buttonType === 'is-outlined',
        'is-text': this.buttonType === 'is-text'
      }
    }
  },
  methods: {
    onClick(event) {
      this.$emit('click', event)
    }
  }
}
</script>
<style scoped>
.c-Button {
  cursor: pointer;
  display: flex;
  align-items: center;
  height: 32px;
  padding: 0 16px;
  border: none;
  border-radius: 4px;
  position: relative;
}

.c-Button::before {
  content: '';
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  border-radius: 4px;
  z-index: 1;
  opacity: 0;
  transition: opacity 0.15s ease-in-out;
  background-color: black;
}

.c-Button:hover::before  {
  opacity: 0.1;
}

.c-Button:active::before {
  opacity: 0.2;
}

.c-Button__label {
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 1.25px;
}
</style>
