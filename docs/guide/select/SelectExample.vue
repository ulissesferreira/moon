<template>
  <p>Selected value: {{ selectedValue }}</p>
  <Select label="Select" :items="items" v-model="selectedValue"/>
</template>
<script>
import { Select } from '../../../src/index'

export default {
  name: 'SelectExample',
  components: {
    Select
  },
  data() {
    return {
      items: [{
        label: 'Label 1',
        value: 'value1'
      }, {
        label: 'Label 2',
        value: 'value2'
      }],
      selectedValue: 'value1'
    }
  },
}
</script>
