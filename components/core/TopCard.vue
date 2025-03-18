<template>
  <div class="top-card">
    <slot></slot>
  </div>
</template>

<style scoped>
.top-card {
  border-radius: var(--radius-large);
  padding: var(--spacing-lg);
}

.top-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 12px 28px rgba(0, 0, 0, 0.2);
}
</style> 