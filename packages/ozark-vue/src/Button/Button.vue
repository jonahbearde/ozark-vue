<script lang="ts">
import { tv, type VariantProps } from 'tailwind-variants'

const button = tv({
  base: 'border-2',
  variants: {
    variant: {
      outline: 'border-gray-300',
      solid: 'bg-blue-500',
    },
  },
})

type ButtonVariantProps = VariantProps<typeof button>

export interface ButtonProps {
  label?: string
  variant?: ButtonVariantProps['variant']
}
</script>

<script setup lang="ts">
withDefaults(defineProps<ButtonProps>(), {
  variant: 'solid',
})
</script>

<template>
  <div>
    <button :class="button({ variant })">
      <slot>
        {{ label }}
      </slot>
    </button>
  </div>
</template>
