<template>
  <div class="kontakt-item">
    <div class="content">
      <h3 class="title">{{ title }}</h3>
      <slot></slot>
    </div>
  </div>
</template>

<script setup>
defineProps({
  title: {
    type: String,
    required: true
  }
});
</script>

<style scoped>
.kontakt-item {
  display: flex;
  flex-direction: column;
  align-items: start;
  text-align: start;
  gap: var(--spacing-sm);
  margin-bottom: var(--spacing-lg);
}

.title {
  color: var(--color-primary);
  font-size: 1.2rem;
  margin-bottom: var(--spacing-xs);
  font-weight: var(--font-weight-bold);
  opacity: 0.5;
}

.content {
  width: 100%;
}

@media (max-width: 768px) {
  .kontakt-item {
    padding: var(--spacing-xs);
  }
}
</style> 