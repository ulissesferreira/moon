<template>
  <p>State: {{ state }}</p>
  <Checkbox label="Checkbox" v-model="state"/>
</template>
<script>
import { Checkbox } from '../../../src/index'

export default {
  name: 'CheckboxExample',
  components: {
    Checkbox
  },
  data() {
    return {
      state: true,
    }
  }
}
</script>
