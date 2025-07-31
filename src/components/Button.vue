<script setup lang="ts">
import { vAutoAnimate } from '@formkit/auto-animate/vue'

defineProps<{
  loading?: boolean
  disabled?: boolean
}>()
</script>

<template>
  <button
    ref="button"
    class="flex cursor-pointer items-center justify-center gap-2 rounded bg-amber-500 px-4 py-2 text-white disabled:cursor-not-allowed disabled:opacity-50"
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
