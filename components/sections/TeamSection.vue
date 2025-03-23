<template>
  <section id="team" class="team-section">
    <div class="container">
      <SectionHeading 
        title="Unser Team" 
        subtitle="Lernen Sie unser erfahrenes Team von Gesundheitsexperten kennen"
      />
      
      <div class="team-grid">
        <TeamItem 
          v-for="(member, index) in teamMembers" 
          :key="index"
          :image="member.image"
          :name="member.name"
          :position="member.position"
        />
      </div>
    </div>
  </section>
</template>

<script setup>
import SectionHeading from '../core/SectionHeading.vue';
import TeamItem from './TeamItem.vue';
import { useTeamMembers } from '../../composables/useTeamMembers';

const { teamMembers } = useTeamMembers();
</script>

<style scoped>
.team-section {
  padding: var(--spacing-xxl) 0;
  background-color: var(--color-background);
}

.team-grid {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: var(--spacing-md);
}

@media (max-width: 1200px) {
  .team-grid {
    grid-template-columns: repeat(4, 1fr);
  }
}

@media (max-width: 1000px) {
  .team-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

@media (max-width: 768px) {
  .team-section {
    position: relative;
    overflow: hidden;
    width: 100%;
  }
  
  /* Team grid that extends beyond the viewport */
  .team-grid {
    display: flex;
    flex-wrap: nowrap;
    overflow-x: auto;
    scroll-behavior: smooth;
    scroll-padding-left: var(--spacing-md);
    -webkit-overflow-scrolling: touch;
    gap: var(--spacing-xs);
    padding-bottom: var(--spacing-md);
    
    /* Make grid wider than container and center it */
    width: calc(100% + 80px);
    margin-left: -40px; 
    padding-left: 40px;
    padding-right: 40px;
  }
  
  
  .team-grid {
    /* Standard scrollbar properties (Firefox) */
    scrollbar-width: thin;
    scrollbar-color: var(--color-accent-green) var(--color-background-light);
  }

  /* WebKit specific scrollbar styling (Chrome, Safari, newer Edge) */
  .team-grid::-webkit-scrollbar {
    height: 8px;
  }

  .team-grid::-webkit-scrollbar-track {
    background: var(--color-background-light);
    border-radius: 4px;
  }

  .team-grid::-webkit-scrollbar-thumb {
    background: var(--color-accent-green);
    border-radius: 4px;
  }

  .team-grid > * {
    flex: 0 0 200px;
    scroll-snap-align: start;
  }
}
</style> 