<template>
  <div class="container">
    <div class="top-card">
      <div class="hero-section-text">
        <motion.h1
        :whileHover="{ scale: 1.1 }"
        :whileDrag="{ scale: 0.9, rotate: 5 }"
        drag
        >01PrePage - Doctor's Office</motion.h1>
        <p>Ihre Gesundheit liegt uns am Herzen</p>
        <Button>Kontakt</Button>
      </div>
      <div class="hero-section-item">
        <Hero4Pictures />
      </div>
    </div>
  </div>
</template>

<script setup>
import Button from '~/components/core/Button.vue';
import Hero4Pictures from '~/components/HeroItems/Hero4Pictures.vue';
import { motion } from "motion-v"
</script>

<style scoped>
.top-card {
  color: var(--color-primary);
  margin-top: 10rem;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  height: 50vh;
  gap: var(--spacing-xl);
}

.hero-section-text {
  align-self: flex-start;
  padding-top: 6rem;
  gap: var(--spacing-md);
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  
}



@media (max-width: 768px) {
  .hero-section h1 {
    font-size: 2rem;
  }
  
  .hero-section p {
    font-size: 1.2rem;
  }
}
</style> 
