<template>
  <BaseCard :elevated="true" class="leistung-item">
    <h3 class="title">{{ title }}</h3>
    <p class="description">{{ description }}</p>
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
  }
});
</script>

<style scoped>
.leistung-item {
  height: 100%;
  display: flex;
  flex-direction: column;
  padding: var(--spacing-md);
  transition: transform 0.3s ease;
}

.leistung-item:hover {
  transform: translateY(-5px);
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
}
</style> 