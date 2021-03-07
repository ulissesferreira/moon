<template>
  <label
    class="c-Switch"
    tabindex="0"
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
  </label>
</template>
<script>
export default {
  name: 'Switch',
  props: {
    label: {
      type: String,
      required: true,
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
.c-Switch {
  position: relative;
  display: inline-block;
  width: 48px;
  height: 24px;
}

.c-Switch input {
  display: none;
}

.c-Switch__slider {
  border-radius: 24px;
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #ccc;
  -webkit-transition: 0.150s;
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
  -webkit-transition: 0.150s;
  transition: 0.150s;
}

.c-Switch__input:checked + .c-Switch__slider {
  background-color: #101010;
}

.c-Switch__input:focus + .c-Switch__slider {
  box-shadow: 0 0 1px #101010;
}

.c-Switch__input:checked + .c-Switch__slider:before {
  -webkit-transform: translateX(24px);
  -ms-transform: translateX(24px);
  transform: translateX(24px);
}
</style>
