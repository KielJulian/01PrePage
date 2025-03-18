<template>
  <BaseCard :elevated="true" class="leistung-item">
    <div class="icon-container" :style="{ backgroundColor: iconBgColor }">
      <img v-if="icon" :src="icon" :alt="title" class="icon">
      <div v-else class="icon-placeholder"></div>
    </div>
    <h3 class="title">{{ title }}</h3>
    <p class="description">{{ description }}</p>
    <div class="cta" v-if="ctaText">
      <a href="#" class="learn-more">{{ ctaText }} →</a>
    </div>
  </BaseCard>
</template>

<script setup>
import BaseCard from '../core/BaseCard.vue';

defineProps({
  icon: {
    type: String,
    default: ''
  },
  iconBgColor: {
    type: String,
    default: 'var(--color-highlight-mint)'
  },
  title: {
    type: String,
    required: true
  },
  description: {
    type: String,
    required: true
  },
  ctaText: {
    type: String,
    default: 'Mehr erfahren'
  }
});
</script>

<style scoped>
.leistung-item {
  height: 100%;
  display: flex;
  flex-direction: column;
}


.icon-container {
  width: 70px;
  height: 70px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: var(--spacing-md);
}

.icon {
  width: 35px;
  height: 35px;
  object-fit: contain;
}

.icon-placeholder {
  width: 35px;
  height: 35px;
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 50%;
}

.title {
  color: var(--color-primary);
  font-size: 1.5rem;
  margin-bottom: var(--spacing-sm);
}

.description {
  flex-grow: 1;
  margin-bottom: var(--spacing-md);
  color: #555;
}

.learn-more {
  color: var(--color-primary);
  font-weight: 600;
  transition: color 0.3s ease;
}

.learn-more:hover {
  color: var(--color-accent-green);
}
</style> 