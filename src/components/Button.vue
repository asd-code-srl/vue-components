<script setup lang="ts">
import { vAutoAnimate } from '@formkit/auto-animate/vue'

withDefaults(
  defineProps<{
    loading?: boolean
    disabled?: boolean
    fullWidth?: boolean
    color?: 'default' | 'error'
  }>(),
  {
    color: 'default',
  },
)
</script>

<template>
  <button
    ref="button"
    class="flex cursor-pointer items-center justify-center gap-2 rounded px-4 py-2 text-white disabled:cursor-not-allowed disabled:opacity-50"
    :class="{
      'w-full': fullWidth,
      'bg-primary-500': color === 'default',
      'bg-error-500': color === 'error',
    }"
    :disabled="disabled || loading"
  >
    <div v-auto-animate>
      <div
        v-if="loading"
        class="h-4 w-4 animate-spin rounded-full border-2 border-white border-t-transparent"
      />
    </div>
    <slot />
  </button>
</template>
