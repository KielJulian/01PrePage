<template>
  <div class="hero-team-preview">
    <div class="team-images" :class="{'mobile-only': isMobile}">
      <!-- Desktop version -->
      <div 
        v-if="!isMobile"
        v-for="(member, index) in teamMembers" 
        :key="index" 
        class="team-image-wrapper"
        :style="{ zIndex: teamMembers.length - index }"
      >
        <img 
          :src="member.image" 
          :alt="member.name"
          class="team-image"
        />
      </div>
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
      <p class="team-tagline">Unser Team ist für Sie da – kompetent, herzlich und engagiert.</p>
      <a @click.prevent="scrollToTeam" class="team-link">Unser Team kennenlernen →</a>
    </div>
  </div>
</template>

<script setup>
import { useTeamMembers } from '../../composables/useTeamMembers';
import { ref, onMounted, onBeforeUnmount } from 'vue';

const { teamMembers } = useTeamMembers();
const isMobile = ref(false);

const scrollToTeam = () => {
  const teamSection = document.querySelector('#team');
  if (teamSection) {
    const rect = teamSection.getBoundingClientRect();
    const scrollTop = window.pageYOffset || document.documentElement.scrollTop;
    const targetPosition = scrollTop + rect.top - 100; // 100px offset
    window.scrollTo({
      top: targetPosition,
      behavior: 'smooth'
    });
  }
};

const checkIfMobile = () => {
  if (typeof window === 'undefined') return;
  isMobile.value = window.innerWidth <= 480;
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
  width: calc(100% + 32px);
  padding-left: 16px;
  padding-right: 16px;
  overflow: hidden;
}

.scroll-track {
  display: flex;
  position: absolute;
  animation: scroll 40s linear infinite;
  gap: var(--spacing-xs);
  overflow: hidden;
}

.mobile-image {
  flex-shrink: 0;
  width: 70px;
  height: 70px;
}

@keyframes scroll {
  0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(calc(-100% / 2));
  }
}

@media (max-width: 480px) {
  .team-images {
    display: none;
  }
}

@media (max-width: 630px) {
    .team-image-wrapper {
        margin-left: -35px;
    }
}
</style>
