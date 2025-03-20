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
}

.title {
  color: var(--color-primary);
  font-size: 1.5rem;
  margin-bottom: var(--spacing-sm);
}

.description {
  flex-grow: 1;
  color: #555;
}
</style> 