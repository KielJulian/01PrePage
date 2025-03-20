<template>
  <div class="kontakt-item">
    <div class="icon-container">
      <slot name="icon"></slot>
    </div>
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

.icon-container {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background-color: var(--color-highlight-purple);
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--color-white);
  font-size: 1.2rem;
  margin-bottom: var(--spacing-xs);
}

.title {
  color: var(--color-highlight-purple);
  font-size: 1.2rem;
  margin-bottom: var(--spacing-xs);
  font-weight: var(--font-weight-bold);
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