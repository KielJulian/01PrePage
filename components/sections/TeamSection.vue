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

const teamMembers = [
  {
    name: 'Dr. Martina Weber',
    position: 'Leitende Ärztin',
    image: '/img/team/Dr-Martina-Weber.jpg'
  },
  {
    name: 'Dr. Thomas Merano',
    position: 'Kardiologe',
    image: '/img/team/Dr-Thomas-Müller.jpg'
  },
  {
    name: 'Dr. Sophie Becker',
    position: 'Dermatologin',
    image: '/img/team/Dr-Sophie-Becker.jpg'
  },
  {
    name: 'Marion Schmidt',
    position: 'Fachangestellte',
    image: '/img/team/Marion-Schmidt.jpg'
  },
  {
    name: 'Maria Garcia',
    position: 'Ernährungsberaterin',
    image: '/img/team/maria-garcia.jpg'
  },
  {
    name: 'Dr. Albert Dera',
    position: 'Neurologe',
    image: '/img/team/albert-dera.jpg'
  },
  {
    name: 'Polova Hans',
    position: 'Physiotherapeut',
    image: '/img/team/polova-hans.jpg'
  },
  {
    name: 'Jurica Mensen',
    position: 'Psychotherapeut',
    image: '/img/team/jurica-mensen.jpg'
  },
  {
    name: 'Darshan Patel',
    position: 'Orthopäde',
    image: '/img/team/darshan-patel.jpg'
  }
];
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
    scroll-snap-type: x mandatory;
    scroll-behavior: smooth;
    scroll-padding-left: 20px;
    -webkit-overflow-scrolling: touch;
    gap: var(--spacing-md);
    padding-bottom: var(--spacing-md);
    
    /* Make grid wider than container and center it */
    width: calc(100% + 80px); /* Extend beyond container */
    margin-left: -40px; /* Pull left side out of view */
    padding-left: 40px; /* Add padding for first item spacing */
    padding-right: 40px; /* Add padding for last item spacing */
  }
  
  
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