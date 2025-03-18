<template>
  <section id="kontakt" class="kontakt-section">
    <div class="container">
      <SectionHeading 
        title="Kontakt" 
        subtitle="Wir sind für Sie da. Nehmen Sie Kontakt mit uns auf."
      />
      
      <div class="kontakt-content">
        <div class="kontakt-info">
          <KontaktItem title="Adresse">
            <template #icon>
              <span>📍</span>
            </template>
            <p>Musterstraße 123<br>12345 Musterstadt</p>
          </KontaktItem>
          
          <KontaktItem title="Telefon">
            <template #icon>
              <span>📞</span>
            </template>
            <p><a href="tel:+491234567890">+49 (0) 123 456 7890</a></p>
          </KontaktItem>
          
          <KontaktItem title="E-Mail">
            <template #icon>
              <span>✉️</span>
            </template>
            <p><a href="mailto:info@01prepage.de">info@01prepage.de</a></p>
          </KontaktItem>
          
          <KontaktItem title="Öffnungszeiten">
            <template #icon>
              <span>🕒</span>
            </template>
            <div class="opening-hours">
              <div class="day-time">
                <span class="day">Montag - Freitag:</span>
                <span class="time">08:00 - 18:00 Uhr</span>
              </div>
              <div class="day-time">
                <span class="day">Samstag:</span>
                <span class="time">09:00 - 13:00 Uhr</span>
              </div>
              <div class="day-time">
                <span class="day">Sonntag:</span>
                <span class="time">Geschlossen</span>
              </div>
            </div>
          </KontaktItem>
        </div>
        
        <div class="map-container">
          <TopCard>
            <div v-if="!showMap" class="map-placeholder">
              <p>Google Maps Einbettung</p>
              <p>Aus Datenschutzgründen wird die Karte erst nach Ihrer Zustimmung geladen.</p>
              <Button @click="loadMap">Karte laden</Button>
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
          </TopCard>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';
import SectionHeading from '../core/SectionHeading.vue';
import KontaktItem from './KontaktItem.vue';
import TopCard from '../core/TopCard.vue';
import Button from '../core/Button.vue';

const showMap = ref(false);
const mapUrl = "https://www.google.com/maps/embed?pb=!1m17!1m12!1m3!1d2366.107498526846!2d8.665461376775237!3d53.64200057169095!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m2!1m1!2zNTPCsDM4JzMxLjIiTiA4wrA0MCcwMi4xIkU!5e0!3m2!1sde!2sde!4v1715095183370!5m2!1sde!2sde";

function loadMap() {
  showMap.value = true;
}
</script>

<style scoped>
.kontakt-section {
  padding: var(--spacing-xxl) 0;
}

.kontakt-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: var(--spacing-xl);
}

.opening-hours {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-xs);
}

.day-time {
  display: flex;
  justify-content: space-between;
}

.day {
  font-weight: 600;
}

.time {
  color: #555;
}

.map-container {
  height: 100%;
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

a {
  color: var(--color-primary);
  text-decoration: none;
  transition: color 0.3s ease;
}

a:hover {
  color: var(--color-accent-green);
}

@media (max-width: 992px) {
  .kontakt-content {
    grid-template-columns: 1fr;
  }
  
  .map-container {
    order: -1;
  }
  
  .map-placeholder {
    height: 300px;
  }
}

@media (max-width: 576px) {
  .day-time {
    flex-direction: column;
    align-items: center;
    gap: 4px;
  }
}
</style>