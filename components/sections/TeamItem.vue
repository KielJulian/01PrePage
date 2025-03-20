<template>
  <div class="team-item">
    <div class="image-container">
      <img v-if="image" :src="image" :alt="name" class="team-image">
      <div v-else class="image-placeholder"></div>
    </div>
    <div class="team-info">
      <h3 class="name">{{ name }}</h3>
      <p class="position">{{ position }}</p>
    </div>
  </div>
</template>

<script setup>
defineProps({
  image: {
    type: String,
    default: ''
  },
  name: {
    type: String,
    required: true
  },
  position: {
    type: String,
    required: true
  },
});
</script>

<style scoped>
.team-item {
  background-color: var(--color-white);
  border-radius: var(--radius-small);
  border: 1px solid var(--color-card-boarder);
  overflow: hidden;
  box-shadow: var(--box-card);
  padding: var(--spacing-sm);
  height: 100%;
}

.image-container {
  height: 200px;
  overflow: hidden;
  padding-top: 120%;
  position: relative;
}

.team-image {
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 100%;
  max-width: 100%;
  height: auto;
  object-fit: cover;
  border-radius: var(--radius-small);
  filter: grayscale(100%);
}


.team-info {
  padding-top: var(--spacing-sm);
}

.name {
  color: var(--color-primary);
  font-size: var(--font-size-sm);
}

.position {
  color: var(--color-accent-green);
  font-weight: 600;
  font-size: 0.9rem;
}

.specialty-tag {
  background-color: var(--color-highlight-purple);
  color: var(--color-primary);
  font-size: 0.8rem;
  padding: 4px 10px;
  border-radius: 20px;
  font-weight: 500;
}

@media (max-width: 768px) {
  .team-item {
    width: 200px;
    min-width: 200px;
  }
  
  .image-container {
    height: 160px;
    padding-top: 110%;
  }
  
  .team-info {
    padding-top: var(--spacing-xs);
  }
  
  .name {
    font-size: 0.95rem;
  }
  
  .position {
    font-size: 0.85rem;
  }
}
</style> 