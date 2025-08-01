<script setup lang="ts">
import { vAutoAnimate } from '@formkit/auto-animate/vue'

withDefaults(
  defineProps<{
    loading?: boolean
    disabled?: boolean
    fullWidth?: boolean
    color?: 'default' | 'secondary' | 'error' | 'warning' | 'success' | 'info'
    rounded?: 'none' | 'sm' | 'md' | 'lg' | 'full'
    variant?: 'solid' | 'outline' | 'ghost' | 'text'
    size?: 'sm' | 'md' | 'lg'
  }>(),
  {
    color: 'default',
    rounded: 'md',
    variant: 'solid',
    size: 'sm',
  },
)
</script>

<template>
  <button
    v-auto-animate
    ref="button"
    :aria-disabled="disabled || loading"
    :aria-busy="loading"
    class="flex cursor-pointer items-center justify-center gap-2 disabled:cursor-not-allowed disabled:opacity-50"
    :class="[
      {
        'w-full': fullWidth,
        'bg-primary-500': color === 'default',
        'bg-error-500': color === 'error',
        'bg-warning-500': color === 'warning',
        'bg-info-500': color === 'info',
        'bg-secondary-500': color === 'secondary',
      },
      //rounded
      {
        'rounded-none': rounded === 'none',
        'rounded-sm': rounded === 'sm',
        'rounded-md': rounded === 'md',
        'rounded-lg': rounded === 'lg',
        'rounded-full': rounded === 'full',
      },
      //variant-solid
      {
        'bg-primary-500 hover:bg-primary-600 focus:ring-primary-300 text-white':
          color === 'default' && variant === 'solid',
        'bg-error-500 hover:bg-error-600 focus:ring-error-300 text-white':
          color === 'error' && variant === 'solid',
        'bg-warning-500 hover:bg-warning-600 focus:ring-warning-300 text-white':
          color === 'warning' && variant === 'solid',
        'bg-info-500 hover:bg-info-600 focus:ring-info-300 text-white':
          color === 'info' && variant === 'solid',
        'bg-secondary-500 hover:bg-secondary-600 focus:ring-secondary-300 text-white':
          color === 'secondary' && variant === 'solid',
      },
      //variant-outline
      {
        'text-primary-500 border-primary-500 hover:bg-primary-50 focus:ring-primary-300 border bg-transparent':
          color === 'default' && variant === 'outline',
        'text-error-500 border-error-500 hover:bg-error-50 focus:ring-error-300 border bg-transparent':
          color === 'error' && variant === 'outline',
        'text-warning-500 border-warning-500 hover:bg-warning-50 focus:ring-warning-300 border bg-transparent':
          color === 'warning' && variant === 'outline',
        'text-info-500 border-info-500 hover:bg-info-50 focus:ring-info-300 border bg-transparent':
          color === 'info' && variant === 'outline',
        'text-secondary-500 border-secondary-500 hover:bg-secondary-50 focus:ring-secondary-300 border bg-transparent':
          color === 'secondary' && variant === 'outline',
      },
      //variant-ghost
      {
        'text-primary-500 hover:bg-primary-50 focus:ring-primary-300 bg-transparent':
          color === 'default' && variant === 'ghost',
        'text-error-500 hover:bg-error-50 focus:ring-error-300 bg-transparent':
          color === 'error' && variant === 'ghost',
        'text-warning-500 hover:bg-warning-50 focus:ring-warning-300 bg-transparent':
          color === 'warning' && variant === 'ghost',
        'text-info-500 hover:bg-info-50 focus:ring-info-300 bg-transparent':
          color === 'info' && variant === 'ghost',
        'text-secondary-500 hover:bg-secondary-50 focus:ring-secondary-300 bg-transparent':
          color === 'secondary' && variant === 'ghost',
      },
      //variant-text
      {
        'text-primary-500 focus:ring-primary-300 bg-transparent hover:underline':
          color === 'default' && variant === 'text',
        'text-error-500 focus:ring-error-300 bg-transparent hover:underline':
          color === 'error' && variant === 'text',
        'text-warning-500 focus:ring-warning-300 bg-transparent hover:underline':
          color === 'warning' && variant === 'text',
        'text-info-500 focus:ring-info-300 bg-transparent hover:underline':
          color === 'info' && variant === 'text',
        'text-secondary-500 focus:ring-secondary-300 bg-transparent hover:underline':
          color === 'secondary' && variant === 'text',
      },
      //size
      {
        'px-2 py-1 text-sm': size === 'sm',
        'px-4 py-2 text-base': size === 'md',
        'px-6 py-3 text-lg': size === 'lg',
      },
    ]"
    :disabled="disabled || loading"
  >
    <template v-if="loading">
      <div
        class="h-4 w-4 animate-spin rounded-full border-2 border-current border-t-transparent"
      />
    </template>
    <template v-else>
      <slot name="leftIcon" />
    </template>
    <slot />
    <slot name="rightIcon" />
  </button>
</template>
