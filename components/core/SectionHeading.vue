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
  color: var(--color-accent-green);
  font-weight: var(--font-weight-regular);
  font-size: var(--font-size-2xl);
  position: relative;
  display: inline-block;
}


.subtitle {
  opacity: 0.75;
  /* color: #666;
  font-size: 1.2rem;
  max-width: 600px; */
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