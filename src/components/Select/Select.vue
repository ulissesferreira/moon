<template>
  <div ref="select" class="c-Select" tabindex="0" @click="triggerMenu()">
    <span class="c-Select__label">{{ label }}</span>
    <ul
      class="c-Select__dropdown"
      id="selectMenu"
      tabindex="0"
      ref="menu"
    >
      <li class="c-Select__item" tabindex="0">
        <span>Hello</span>
      </li>
      <li class="c-Select__item" tabindex="0">
        <span>Hello</span>
      </li>
    </ul>
  </div>
</template>
<script>
import tippy from 'tippy.js';
import 'tippy.js/dist/tippy.css';

export default {
  name: 'Select',
  props: {
    label: {
      type: String,
      required: false,
      default: undefined
    },
    modelValue: {
      type: String,
      required: false,
      default: undefined,
    },
    name: {
      type: String,
      required: false,
      default: undefined
    },
    items: {
      type: Array,
      required: true,
      validator: (items) => {
				let isValid = true

				items.forEach((item) => {
					isValid &&= 'label' in item && 'value' in item
				})

				return isValid
			}
    },
    disabled: {
      type: Boolean,
      required: false,
      default: false,
    }
  },
  data() {
    return {
      selectedValue: this.modelValue,
      isMenuOpen: false,
    }
  },
  computed: {
    selectClassObject() {
      return {
        'has-value': ''
      }
    }
  },
  mounted() {
    const element = document.getElementById('selectMenu')
    tippyInstance = tippy(this.$refs.select, {
      theme: 'select',
      interactive: true,
      appendTo: this.$refs.select,
      content: element,
      arrow: false,
      trigger: 'click',
      placement: 'bottom',
    })
  },
  methods: {
    triggerMenu() {
      this.isMenuOpen = !this.isMenuOpen
    }
  }
}
</script>
<style>
[data-tippy-root] {
  width: 100%;
}

.tippy-box[data-theme~='select'] {
  max-width: unset !important;
  width: 100%;
  background-color: white;
  color: black;
  border: 1px solid black;
}

.tippy-box[data-theme~='select'] .tippy-content {
  padding: 0;
}
</style>
<style scoped>
.c-Select {
  height: 48px;
  width: 100%;
  outline: none;
  border: 1px solid black;
  border-radius: 4px;
  background-color: transparent;
  font-size: 16px;
  color: black;
  padding: 8px;
  cursor: pointer;
  position: relative;
  transition:
    border 150ms ease-in-out,
    box-shadow 150ms ease-in-out;
}

.c-Select__label {
  display: block;
  font-size: 16px;
  color: black;
  cursor: pointer;
  position: absolute;
  top: 12px;
  left: 9px;
  z-index: 2;
  transition: 150ms ease-in-out;
}

.c-Select__dropdown {
  display: flex;
  flex-direction: column;
  width: 100%;
  margin: 0;
  padding: 0;
  list-style: none;
  overflow: hidden;
}

.c-Select__dropdown:first-child {
  border-top-left-radius: 4px;
  border-top-right-radius: 4px
}

.c-Select__dropdown:last-child {
  border-bottom-left-radius: 4px;
  border-bottom-right-radius: 4px
}

.c-Select__item {
  height: 32px;
  padding: 8px;
  display: flex;
  align-items: center;
}

.c-Select__item:hover,
.c-Select__item:focus {
  background-color: #E0E0E0;
}
</style>
