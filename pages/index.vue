<template>
  <div>
    <div class="hero-section">
      <div class="container">
        <h1>01PrePage - Doctor's Office</h1>
        <p>Ihre Gesundheit liegt uns am Herzen</p>
      </div>
    </div>
    
    <LeistungSection />
    <PraxisSection />
    <TeamSection />
    <KontaktSection />
    <MapSection />
  </div>
</template>

<script setup>
import LeistungSection from '~/components/sections/LeistungSection.vue';
import PraxisSection from '~/components/sections/PraxisSection.vue';
import TeamSection from '~/components/sections/TeamSection.vue';
import KontaktSection from '~/components/sections/KontaktSection.vue';
import MapSection from '~/components/sections/MapSection.vue';

definePageMeta({
  layout: 'default'
})
</script>

<style scoped>
.hero-section {
  color: var(--color-primary);
  min-height: 70vh;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: var(--spacing-xl) var(--spacing-md);
}

.hero-section h1 {
  font-size: 3rem;
  margin-bottom: var(--spacing-md);
}

.hero-section p {
  font-size: 1.5rem;
  max-width: 600px;
  margin: 0 auto;
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