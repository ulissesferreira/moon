# Select

Select

```js
const items = [{
    label: 'Label 1',
    value: 'value1'
}, {
    label: 'Label 2',
    value: 'value2'
}];
```

```vue
<p>Selected value: {{ selectedValue }}</p>
<Select label="Select" :items="items" v-model="selectedValue"/>
```

<SelectExample />

<script setup>
import SelectExample from './SelectExample.vue'
</script>
