<template>
  <div class="hero-team-preview">
    <div class="team-images" :class="{'mobile-only': isMobile}">
      <!-- Desktop version -->
      <motion.div 
        v-if="!isMobile"
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

    <!-- Mobile version with CSS animation -->
    <div v-if="isMobile" class="mobile-scroller">
      <div class="scroll-track">
        <div 
          v-for="(member, index) in [...teamMembers, ...teamMembers]" 
          :key="`mobile-${index}`"
          class="mobile-image"
        >
          <img 
            :src="member.image" 
            :alt="member.name"
            class="team-image"
          />
        </div>
      </div>
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
import { ref, onMounted, onBeforeUnmount } from 'vue';

const { teamMembers } = useTeamMembers();
const isMobile = ref(false);

const checkIfMobile = () => {
  if (typeof window === 'undefined') return;
  isMobile.value = window.innerWidth <= 768;
};

onMounted(() => {
  checkIfMobile();
  window.addEventListener('resize', checkIfMobile);
});

onBeforeUnmount(() => {
  window.removeEventListener('resize', checkIfMobile);
});
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

/* Mobile scrolling animation */
.mobile-scroller {
  width: 100%;
  height: 90px;
  position: relative;
  overflow: hidden;
  margin-bottom: 20px;
  width: calc(100% + 80px);
    margin-left: -40px; 
    padding-left: 40px;
    padding-right: 40px;

}

.scroll-track {
  display: flex;
  position: absolute;
  animation: scroll 40s linear infinite;
  gap: var(--spacing-sm);
}

.mobile-image {
  flex-shrink: 0;
  width: 70px;
  height: 70px;
  margin-right: 20px;
  filter: drop-shadow(0 4px 6px rgba(0, 0, 0, 0.1));
}

@keyframes scroll {
  0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(calc(-100% / 2));
  }
}

/* @media (max-width: 768px) {
  .hero-team-preview {
    overflow-x: hidden;
  }
  
  .mobile-only {
    display: none;
  }
} */
</style>
