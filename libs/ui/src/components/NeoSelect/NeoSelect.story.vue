<template>
  <Story>
    <NeoSelect
      :placeholder="placeholder"
      :options="options"
    />
  </Story>
</template>

<script lang="ts" setup>
import NeoSelect from './NeoSelect.vue'

const placeholder = 'Select...'
const options = [
  { value: 'opt1', text: 'Option1' },
  { value: 'opt2', text: 'Option2' },
  { value: 'opt3', text: 'Option3' },
]
</script>
