<template>
  <div class="hero-team-preview">
    <div class="team-images">
      <motion.div 
        v-for="(member, index) in teamMembers" 
        :key="index" 
        class="team-image-wrapper"
        :style="{ zIndex: teamMembers.length - index }"
        :initial="{ y: 0 }"
        :whileHover="{ 
          x: 20, 
          y: -20, 
          scale: 1.1,
          zIndex: 10,
          transition: { duration: 0.1 } 
        }"
        :whileInView="{ 
          opacity: 1,
          x: 0,
          transition: { 
            type: 'spring',
            stiffness: 100,
            damping: 10
          }
        }"
        :initial-opacity="0"
        :initial-x="20"
      >
        <img 
          :src="member.image" 
          :alt="member.name"
          class="team-image"
        />
      </motion.div>
    </div>
    <div class="team-text">
      <p class="team-tagline">Mit Erfahrung und Herz ins Leben gerufen – für Ihre Gesundheit</p>
      <a href="#team" class="team-link">Unser Team kennenlernen →</a>
    </div>
  </div>
</template>

<script setup>
import { useTeamMembers } from '../../composables/useTeamMembers';
import { motion } from 'motion-v';

const { teamMembers } = useTeamMembers();
</script>

<style scoped>
.hero-team-preview {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.5rem;
}

.team-images {
  display: flex;
  justify-content: center;
  height: 80px;
  perspective: 1000px;
}

.team-image-wrapper {
  margin-left: -15px;
  position: relative;
  height: 80px;
  width: 80px;
  will-change: transform;
}

.team-image-wrapper:first-child {
  margin-left: 0;
}

.team-image {
  height: 100%;
  width: 100%;
  object-fit: cover;
  border-radius: 30px;
  border: 3px solid var(--color-white);
  filter: grayscale(100%);
}

.team-text {
  text-align: center;
  color: var(--color-primary);
  font-size: var(--font-size-md);
  font-weight: var(--font-weight-medium);
}

.team-tagline {
    margin-bottom: 0.5rem;
    color: var(--color-primary);
}

.team-link {
  color: var(--color-light-blue);
  text-decoration: none;
  display: inline-block;
}

.team-link:hover {
    color: var(--color-accent-green);
}

@media (max-width: 768px) {
  .hero-team-preview {
    
  }
}
</style>
