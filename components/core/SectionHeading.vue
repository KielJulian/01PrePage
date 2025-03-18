<template>
  <div class="section-heading">
    <h2 class="title">{{ title }}</h2>
    <p v-if="subtitle" class="subtitle">{{ subtitle }}</p>
  </div>
</template>

<script setup>
defineProps({
  title: {
    type: String,
    required: true
  },
  subtitle: {
    type: String,
    default: ''
  }
})
</script>

<style scoped>
.section-heading {
  text-align: start;
  margin-bottom: var(--spacing-xl);
}

.title {
  color: var(--color-primary);
  font-size: 2.5rem;
  margin-bottom: var(--spacing-sm);
  position: relative;
  display: inline-block;
}


.subtitle {
  color: #666;
  font-size: 1.2rem;
  max-width: 600px;
}

@media (max-width: 768px) {
  .title {
    font-size: 2rem;
  }
  
  .subtitle {
    font-size: 1rem;
  }
}
</style> 