# Modal

Modal

```vue
<Button label="Open modal" @click="openModal()" />
<Modal v-if="isOpen" @close="closeModal()">
  <h1>Hello World!</h1>
</Modal>
```

<ModalExample />

<script setup>
import ModalExample from './ModalExample.vue'
</script>
