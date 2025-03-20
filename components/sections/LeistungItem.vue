<template>
  <BaseCard :elevated="true" class="leistung-item">
    <h3 class="title">{{ title }}</h3>
    <p class="description">{{ description }}</p>
    <div v-if="tags && tags.length > 0" class="tag-container">
      <span v-for="tag in tags" :key="tag" class="tag">{{ tag }}</span>
    </div>
  </BaseCard>
</template>

<script setup>
import BaseCard from '../core/BaseCard.vue';

defineProps({
  title: {
    type: String,
    required: true
  },
  description: {
    type: String,
    required: true
  },
  tags: {
    type: Array,
    default: () => []
  }
});
</script>

<style scoped>
.leistung-item {
  height: 100%;
  display: flex;
  flex-direction: column;
  padding: var(--spacing-md);
}

.title {
  color: var(--color-primary);
  font-size: 1.25rem;
  margin-bottom: var(--spacing-sm);
}

.description {
  flex-grow: 1;
  color: var(--color-text, #555);
  font-size: 1rem;
  margin-bottom: var(--spacing-sm);
}

.tag-container {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  margin-top: auto;
}

.tag {
  font-size: 0.75rem;
  padding: 2px 8px;
  border-radius: 12px;
  background-color: var(--color-background-alt, #f5f5f5);
  color: var(--color-text-light, #777);
  border: 1px solid var(--color-border, #e0e0e0);
}
</style> 