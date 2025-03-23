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
    <HeroTeamPreview />
  </div>
</template>

<script setup>
import Button from '~/components/core/Button.vue';
import Hero4Pictures from '~/components/HeroItems/Hero4Pictures.vue';
import { motion } from "motion-v"
import HeroTeamPreview from '~/components/HeroItems/HeroTeamPreview.vue';
</script>

<style scoped>
.container {
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-around;
  height: calc(100svh - (90px + 2 * 4rem));
  margin-top: 4rem;
  margin-bottom: 4rem;
}

h1 {
  color: var(--color-accent-green);
}

p {
  font-weight: var(--font-weight-regular);
  font-size: var(--font-size-xl);
}

.top-card {
  color: var(--color-primary);
  display: flex;
  flex-direction: row;
  justify-content: space-between;
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

.hero-section-item {
  width: 45%;
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
