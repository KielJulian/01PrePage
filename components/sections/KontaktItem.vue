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
  gap: var(--spacing-md);
  margin-bottom: var(--spacing-lg);
}

.icon-container {
  flex-shrink: 0;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background-color: var(--color-highlight-mint);
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--color-primary);
  font-size: 1.5rem;
}

.title {
  color: var(--color-primary);
  font-size: 1.2rem;
  margin-bottom: var(--spacing-xs);
}

.content {
  flex-grow: 1;
}

@media (max-width: 768px) {
  .kontakt-item {
    flex-direction: column;
    align-items: center;
    text-align: center;
  }
  
  .icon-container {
    margin-bottom: var(--spacing-xs);
  }
}
</style> 