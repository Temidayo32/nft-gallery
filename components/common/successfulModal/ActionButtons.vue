<template>
  <div class="flex gap-4">
    <NeoButton
      v-if="secondary"
      class="border-k-grey hover-button w-full"
      :disabled="secondary.disabled"
      rounded
      no-shadow
      @click="$emit('secondary')"
    >
      {{ secondary.label }}
    </NeoButton>

    <NeoButton
      class="hover-button w-full"
      :disabled="primary.disabled"
      :loading="primary.disabled"
      variant="primary"
      rounded
      no-shadow
      loading-with-label
      @click="$emit('primary')"
    >
      {{ primary.disabled ? $t('loading') : primary.label }}
    </NeoButton>
  </div>
</template>

<script setup lang="ts">
import { NeoButton } from '@kodadot1/brick'

export type ActionButton = {
  label: string
  disabled?: boolean
}

defineEmits(['primary', 'secondary'])
defineProps<{
  primary: ActionButton
  secondary?: ActionButton
}>()
</script>
