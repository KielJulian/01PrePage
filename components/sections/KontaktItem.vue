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
  margin-bottom: var(--spacing-xs);
  font-weight: var(--font-weight-regular);
  font-size: var(--font-size-lg);
  border-bottom: 2px solid var(--color-primary);
  width: fit-content;
  padding-bottom: var(--spacing-xs);
}

.content {
  width: 100%;
}


</style> 