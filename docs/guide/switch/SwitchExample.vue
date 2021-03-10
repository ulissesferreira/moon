<template>
  <p>State: {{ state }}</p>
  <Switch label="Switch" v-model="state"/>
</template>
<script>
import { Switch } from '../../../src/index'

export default {
  name: 'SwitchExample',
  components: {
    Switch
  },
  data() {
    return {
      state: false,
    }
  }
}
</script>
