<template>
  <div class="gallery">
    <div class="gallery-item item1">
      <img src="/img/praxis/Empfangsbereich.jpg" alt="Empfangsbereich" />
    </div>
    <div class="gallery-item item2">
      <img src="/img/praxis/Behandlungsraum.jpg" alt="Behandlungsraum" />
    </div>
    <div class="gallery-item item3">
      <img src="/img/praxis/Wartezimmer.jpg" alt="Wartezimmer" />
    </div>
    <div class="gallery-item item4">
      <img src="/img/praxis/Diagnostikraum.jpg" alt="Diagnostikraum" />
    </div>
  </div>
</template>

<script setup>
// No props or logic needed for this simple gallery
</script>

<style scoped>
/* Gallery Container */
.gallery {
  display: flex;
  flex-wrap: wrap;
  gap: var(--spacing-sm);
  width: 100%;
  max-width: 600px;
  margin: 0 auto;
  align-items: stretch;
}

/* Gallery Item Base Styles */
.gallery-item {
  position: relative;
  border-radius: var(--radius-large);
  overflow: hidden;
}

/* Image Styling with Improved Centering */
.gallery-item img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
  display: block;
}

/* Flex Item Sizing and Positioning */
.item1 {
  flex: 0 0 calc(33.333% - var(--spacing-md) * 2/3);
  aspect-ratio: 3/4;
  align-self: flex-end;
}

.item2 {
  flex: 0 0 calc(66.667% - var(--spacing-md) * 1/3);
  aspect-ratio: 16/9;
  align-self: flex-end;
}

.item3 {
  flex: 0 0 calc(66.667% - var(--spacing-md) * 1/3);
  aspect-ratio: 4/3;
  align-self: flex-start;
}

.item4 {
  flex: 0 0 calc(33.333% - var(--spacing-md) * 2/3);
  aspect-ratio: 4/3;
  align-self: flex-start;
}

/* Responsive Adjustments */
@media (max-width: 768px) {
  .gallery {
    display: none;
  }
}
</style>
