<template>
  <div :class="['money', { 'inline-block': inline }]">
    <span v-if="!hideUnit">
      {{ finalValue }}
      {{ displayUnit }}
    </span>
    <span v-else>
      {{ finalValue }}
    </span>
  </div>
</template>

<script lang="ts" setup>
import type { Prefix } from '@kodadot1/static'
import { formatAmountWithRound } from '@/utils/format/balance'
import { chainPropListOf } from '@/utils/config/chain.config'

const props = withDefaults(
  defineProps<{
    value?: number | string
    inline: boolean
    hideUnit?: boolean
    unitSymbol?: string
    prefix?: Prefix
    round?: number
  }>(),
  {
    value: 0,
    unitSymbol: '',
    prefix: undefined,
  },
)

const { decimals, unit } = useChain()

const tokenDecimals = computed(() =>
  props.prefix ? chainPropListOf(props.prefix).tokenDecimals : decimals.value,
)
const displayUnit = computed(
  () =>
    props.unitSymbol
    || (props.prefix ? chainPropListOf(props.prefix).tokenSymbol : unit.value),
)
const finalValue = computed(() =>
  formatAmountWithRound(props.value, tokenDecimals.value, props.round),
)
</script>
