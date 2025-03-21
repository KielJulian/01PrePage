<template>
  <div class="leistung-item">
    <h3 class="leistung-title">{{ title }}</h3>
    <p class="leistung-description">{{ description }}</p>
    <div class="leistung-tags">
      <Tag 
        v-for="tag in tags" 
        :key="tag" 
        :text="tag"
      />
    </div>
  </div>
</template>

<script setup>
import Tag from '../core/Tag.vue';

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
  background-color: #fff;
  border-radius: var(--radius-card);
  padding: var(--spacing-md);
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  height: 100%;
  display: flex;
  flex-direction: column;
}

.leistung-item:hover {
  transform: translateY(-3px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.12);
}

.leistung-title {
  color: var(--color-primary);
  margin-top: 0;
  margin-bottom: var(--spacing-xs);
  font-size: var(--font-size-md);
}

.leistung-description {
  margin-bottom: var(--spacing-sm);
  color: var(--color-text);
  font-size: var(--font-size-sm);
  flex-grow: 1;
}

.leistung-tags {
  display: flex;
  flex-wrap: wrap;
  gap: var(--spacing-xs);
  margin-top: auto;
}
</style> 