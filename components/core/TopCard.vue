<template>
  <div class="top-card">
    <slot></slot>
  </div>
</template>

<style scoped>
.top-card {
  background-color: var(--color-white);
  border-radius: var(--radius-large);
  padding: var(--spacing-lg);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.15);
  transition: all 0.3s ease;
}

.top-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 12px 28px rgba(0, 0, 0, 0.2);
}
</style> 