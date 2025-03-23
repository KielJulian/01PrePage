<template>
  <div class="hero-team-preview">
    <div class="team-images">
      <div 
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
    <div class="team-text">
      <p class="team-tagline">Mit Erfahrung und Herz ins Leben gerufen – für Ihre Gesundheit</p>
      <a href="#team" class="team-link">Unser Team kennenlernen →</a>
    </div>
  </div>
</template>

<script setup>
import { useTeamMembers } from '../../composables/useTeamMembers';

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
}

.team-image-wrapper {
  margin-left: -15px;
  position: relative;
  height: 80px;
  width: 80px;
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
  .team-images {
    height: 60px;
  }
  
  .team-image-wrapper {
    height: 60px;
    width: 60px;
    margin-left: -10px;
  }
  
  .team-tagline {
    font-size: 1rem;
  }
  
  .team-link {
    font-size: 0.9rem;
  }
}
</style>
