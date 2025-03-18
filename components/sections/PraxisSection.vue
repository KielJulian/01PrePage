<template>
  <section id="praxis" class="praxis-section">
    <div class="container">
      <SectionHeading 
        title="Unsere Praxis" 
        subtitle="Lernen Sie unsere moderne und komfortable Praxis kennen"
      />
      <div class="praxis-content">       
        <div class="praxis-gallery">
          <div class="gallery-grid">
            <div class="gallery-item">
              <img src="/img/praxis/Empfangsbereich.jpg" alt="Empfangsbereich">
            </div>
            <div class="gallery-item">
              <img src="/img/praxis/Wartezimmer.jpg" alt="Wartezimmer">
            </div>
            <div class="gallery-item">
              <img src="/img/praxis/Behandlungsraum.jpg" alt="Behandlungsraum">
            </div>
            <div class="gallery-item">
              <img src="/img/praxis/Diagnostikraum.jpg" alt="Diagnostikraum">
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import SectionHeading from '../core/SectionHeading.vue';
import Button from '../core/Button.vue';
</script>

<style scoped>
.praxis-section {
  padding: var(--spacing-xxl) 0;
}

.praxis-content {
  display: flex;
  gap: var(--spacing-xl);
  align-items: center;
}

.gallery-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-template-rows: repeat(2, 1fr);
  gap: var(--spacing-lg);
}

.gallery-item {
  border-radius: var(--radius-small);
  overflow: hidden;
  box-shadow: var(--box-card);
  display: flex;
  aspect-ratio: 1 / 1;  
}

.gallery-item img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

@media (max-width: 992px) {
  .praxis-content {
    gap: var(--spacing-lg);
  }
  
  .praxis-description {
    order: 2;
  }
  
  .praxis-gallery {
    order: 1;
  }
}

@media (max-width: 576px) {
  .gallery-grid {
    grid-template-columns: 1fr;
    grid-template-rows: repeat(4, 1fr);
  }
}
</style> 