# Modal

Modal

```vue
<Button label="Open modal" @click="openModal()" />
<Modal v-if="isOpen" @close="closeModal()">
  <div class="o-Modal__example">
    <h1 style="margin: 0px;">Modal example</h1>
    <p>
      You can see that your TAB focus is trapped here. 
      Upon closing, TAB focus will go back to the previously focused element.
    </p>
    <p>
      Lorem ipsum ...
    </p>
    <Button label="Close" @click="closeModal()" />
  </div>
</Modal>
```

<ModalExample />

<script setup>
import ModalExample from './ModalExample.vue'
</script>
