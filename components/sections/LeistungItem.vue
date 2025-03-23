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
  background-color: var(--color-white);
  border-radius: var(--radius-small);
  padding: var(--spacing-md);
  box-shadow: var(--box-shadow-card);
  border: 1px solid var(--color-card-boarder);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  height: 100%;
  display: flex;
  flex-direction: column;
}

.leistung-title {
  color: var(--color-primary);
  margin-top: 0;
  font-size: var(--font-size-sm);
  text-transform: uppercase;
}

.leistung-description {
  color: var(--color-text);
  font-size: var(--font-size-sm);
  flex-grow: 1;
  line-height: var(--line-height-tight);
}

.leistung-tags {
  display: flex;
  flex-wrap: wrap;
  gap: var(--spacing-xs);
  margin-top: var(--spacing-xs);
}
</style> 