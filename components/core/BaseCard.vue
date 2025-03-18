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
}

.elevated {
  border: 1px solid var(--color-card-boarder);
  box-shadow: var(--box-card);
}
</style> 