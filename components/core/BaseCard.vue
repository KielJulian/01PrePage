<template>
  <div class="base-card" :class="{ 'elevated': elevated }">
    <slot></slot>
  </div>
</template>

<script setup>
defineProps({
  elevated: {
    type: Boolean,
    default: false
  }
})
</script>

<style scoped>
.base-card {
  background-color: var(--color-white);
  border-radius: var(--radius-small);
  padding: var(--spacing-md);
  transition: all 0.3s ease;
}

.elevated {
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}
</style> 