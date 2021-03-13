<template>
  <button
    class="c-Button"
    :class="buttonClassObject"
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
    type: {
      type: String,
      required: false,
      default: 'default',
      validator(type) {
        return [
          'default',
          'outlined',
          'text'
        ].includes(type)
      }
    },
    disabled: {
      type: Boolean,
      required: false,
      default: false,
    }
  },
  emits: [
    'click'
  ],
  computed: {
    buttonClassObject() {
      return {
        'is-default': this.type === 'default',
        'is-outlined': this.type === 'outlined',
        'is-text': this.type === 'text'
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

.c-Button.is-default {
  background-color: black;
  border: 1px solid black;
  color: white;
}

.c-Button.is-outlined {
  background-color: transparent;
  border: 1px solid black;
  color: black;
}

.c-Button.is-text {
  background-color: transparent;
  border: none;
  color: black;
}

.c-Button__label {
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 1.25px;
}

.c-Button.is-default:disabled,
.c-Button.is-outlined:disabled,
.c-Button.is-text:disabled {
  border-color: #EEEEEE;
	background-color: #EEEEEE;
  cursor: not-allowed;
}

.c-Button:disabled::before {
  display: none;
}

.c-Button:disabled .c-Button__label {
  color: #757575;
}
</style>
