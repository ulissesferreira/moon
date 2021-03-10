<template>
  <p>Selected value: {{ selectedValue }}</p>
  <Radio name="example" :items="items" v-model="selectedValue"/>
</template>
<script>
import { Radio } from '../../../src/index'

export default {
  name: 'RadioExample',
  components: {
    Radio
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
  }
}
</script>
