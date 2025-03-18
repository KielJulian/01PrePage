<template>
  <div class="team-item">
    <div class="image-container">
      <img v-if="image" :src="image" :alt="name" class="team-image">
      <div v-else class="image-placeholder"></div>
    </div>
    <div class="team-info">
      <h3 class="name">{{ name }}</h3>
      <p class="position">{{ position }}</p>
      <p v-if="description" class="description">{{ description }}</p>
      <div v-if="specialties && specialties.length" class="specialties">
        <span v-for="(specialty, index) in specialties" :key="index" class="specialty-tag">
          {{ specialty }}
        </span>
      </div>
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
  description: {
    type: String,
    default: ''
  },
  specialties: {
    type: Array,
    default: () => []
  }
});
</script>

<style scoped>
.team-item {
  background-color: var(--color-white);
  border-radius: var(--radius-small);
  overflow: hidden;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
  transition: transform 0.3s ease;
}

.team-item:hover {
  transform: translateY(-5px);
}

.image-container {
  height: 250px;
  overflow: hidden;
}

.team-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.5s ease;
}

.team-item:hover .team-image {
  transform: scale(1.05);
}

.image-placeholder {
  width: 100%;
  height: 100%;
  background-color: var(--color-accent-grey);
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--color-white);
  font-size: 1.5rem;
}

.team-info {
  padding: var(--spacing-md);
}

.name {
  color: var(--color-primary);
  font-size: 1.3rem;
  margin-bottom: var(--spacing-xs);
}

.position {
  color: var(--color-accent-green);
  font-weight: 600;
  margin-bottom: var(--spacing-sm);
}

.description {
  color: #555;
  font-size: 0.95rem;
  margin-bottom: var(--spacing-sm);
  line-height: 1.6;
}

.specialties {
  display: flex;
  flex-wrap: wrap;
  gap: var(--spacing-xs);
  margin-top: var(--spacing-sm);
}

.specialty-tag {
  background-color: var(--color-highlight-purple);
  color: var(--color-primary);
  font-size: 0.8rem;
  padding: 4px 10px;
  border-radius: 20px;
  font-weight: 500;
}
</style> 