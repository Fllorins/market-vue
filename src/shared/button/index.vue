<script lang="ts" setup>
import Typography from '@/shared/typography/index.vue'

interface Props {
  color?: 'primary' | 'secondary' | 'greyscale' | 'error'
  decoration?: 'default' | 'outline' | 'none'
  size?: 'L' | 'M' | 'S'
  disabled?: boolean
}

const props = defineProps<Props>()

const { color = 'primary', decoration = 'default', size = 'M', disabled = false } = props

const classes = ['button', `size_${size}`, `decoration_${decoration}`, `color_${color}`]
</script>

<template>
  <button :class="classes" :disabled="disabled">
    <slot name="leftIcon"></slot>
    <Typography tagName="p" size="s" class="button__text"><slot></slot></Typography>
  </button>
</template>

<style scoped>
.button {
  width: 100%;
  display: flex;
  align-items: center;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  margin-left: 40px;
}
.button.size_M {
  gap: 8px;
  padding: 8px;
}
.button.color_secondary {
  background-color: var(--main-secondary);
  color: var(--main-on-secondary);
}
.button__text {
  width: 100%;
  text-align: center;
}
</style>
