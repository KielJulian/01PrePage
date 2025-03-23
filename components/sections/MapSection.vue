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
            style="border:0;" 
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
const mapUrl = "https://www.google.com/maps/embed?pb=!1m17!1m12!1m3!1d2366.107498526846!2d8.665461376775237!3d53.64200057169095!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m2!1m1!2zNTPCsDM4JzMxLjIiTiA4wrA0MCcwMi4xIkU!5e0!3m2!1sde!2sde!4v1715095183370!5m2!1sde!2sde";

function loadMap() {
  showMap.value = true;
}
</script>

<style scoped>
.map-section {
  padding: var(--spacing-xxl) 0;
}

iframe {
  border-radius: var(--radius-small);
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
  background-color: var(--color-accent-grey);
  color: var(--color-primary);
  border-radius: var(--radius-small);
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