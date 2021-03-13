<template>
  <Button label="Open modal" @click="openModal()" />
  <Modal v-if="isOpen" @close="closeModal()">
    <div class="o-Modal__example">
      <Button label="I am focused" @click="closeModal()" disabled />
      <Button label="Focus me next" @click="closeModal()" />
      <input type="text" placeholder="Me as well"/>
    </div>
  </Modal>
</template>
<script>
import { Button, Modal } from '../../../src/index'

export default {
  name: 'ButtonExample',
  components: {
    Button,
    Modal
  },
  data() {
    return {
      isOpen: false,
    }
  },
  methods: {
    openModal() {
      this.isOpen = true
    },
    closeModal() {
      this.isOpen = false
    }
  }
}
</script>
<style scoped>
.o-Modal__example {
  padding: 1rem;
}
</style>
