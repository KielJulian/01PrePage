<template>
  <section id="map" class="map-section">
    <div class="container">     
      <div class="map-container">
          <div v-if="!showMap" class="map-placeholder">
            <p>Google Maps Einbettung</p>
            <p>Aus Datenschutzgründen wird die Karte erst nach Ihrer Zustimmung geladen.</p>
            <Button @click="loadMap" class="btn-secondary">Karte laden</Button>
          </div>
            <iframe 
            v-else
            :src="mapUrl"
            width="100%" 
            height="400" 
            allowfullscreen="" 
            loading="lazy" 
            referrerpolicy="no-referrer-when-downgrade">
          </iframe>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';
import Button from '../core/Button.vue';

const showMap = ref(false);
const mapUrl = "https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d8049.936018240594!2d11.543675352373803!3d48.17390517506173!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x479e77cd0920142b%3A0x8476de5e0c89dc95!2sOlympiapark%20S%C3%BCd!5e0!3m2!1sen!2sde!4v1742746518043!5m2!1sen!2sde";

function loadMap() {
  showMap.value = true;
}
</script>

<style scoped>
.map-section {
  padding: var(--spacing-sm) 0;
  margin-bottom : var(--spacing-3xl);
}

iframe {
  border-radius: var(--radius-large);
  box-shadow: var(--box-shadow-card);
  border: 1px solid var(--color-card-boarder);
}

.map-container {
  max-width: 100%;
  margin: 0 auto;
}

.map-placeholder {
  height: 400px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  background-color: var(--color-black-05);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  color: var(--color-primary);
  border-radius: var(--radius-large);
  padding: var(--spacing-lg);
}

.map-placeholder p {
  margin-bottom: var(--spacing-sm);
}

.map-placeholder button {
  margin-top: var(--spacing-md);
}

@media (max-width: 576px) {
  .map-placeholder {
    height: 300px;
  }
}
</style> 