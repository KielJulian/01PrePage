<template>
  <section id="kontakt" class="kontakt-section">
    <div class="container">
      <SectionHeading 
        title="Kontakt" 
        subtitle="Wir sind für Sie da. Nehmen Sie Kontakt mit uns auf."
      />
      
      <div class="kontakt-items-grid">
  <KontaktItem title="Kontakt">
    <template #icon>
      <span>✓</span>
    </template>
    <ul>
      <li><h6>Telefon</h6></li>
      <li>07743 9213487</li>
      <li><h6>E-Mail</h6></li>
      <li>info@praxis-bergblick.de</li>
      <li><h6>Fax</h6></li>
      <li>07743 9213488</li>
      <li><h6>Adresse</h6></li>
      <li>Lindenweg 23</li>
      <li>78315 Radolfzell</li>
    </ul>
  </KontaktItem>

  <KontaktItem title="Öffnungszeiten">
    <template #icon>
      <span>✓</span>
    </template>
    <ul>
      <li><h6>Montag</h6></li>
      <li>07:30 bis 12:00 Uhr</li>
      <li>15:00 bis 17:30 Uhr</li>
      <li><h6>Dienstag</h6></li>
      <li>07:30 bis 12:00 Uhr</li>
      <li>15:00 bis 17:30 Uhr</li>
      <li><h6>Mittwoch</h6></li>
      <li>07:30 bis 12:00 Uhr</li>
      <li><h6>Donnerstag</h6></li>
      <li>07:30 bis 12:00 Uhr</li>
      <li>15:00 bis 17:30 Uhr</li>
      <li><h6>Freitag</h6></li>
      <li>07:30 bis 12:00 Uhr</li>
    </ul>
  </KontaktItem>
  
  <KontaktItem title="Urlaubszeiten">
    <template #icon>
      <span>✓</span>
    </template>
    <ul>
      <li><h6>2025</h6></li>
      <li>17. Januar – 24. Januar</li>
      <li>5. April – 12. April</li>
      <li>22. Juni – 3. Juli</li>
      <li>14. August – 29. August</li>
      <li>7. Oktober – 15. Oktober</li>
      <li>18. November – 28. November</li>
    </ul>
  </KontaktItem>

  <KontaktItem title="Notfallkontakte">
    <template #icon>
      <span>✓</span>
    </template>
    <ul>
      <li><h6>Notarzt</h6></li>
      <li><em>(lebensbedrohliche Notfälle)</em> 112</li>
      <li><h6>Ärztlicher Bereitschaftsdienst</h6></li>
      <li>116 117</li>
      <li><h6>Zahnärztlicher Notdienst</h6></li>
      <li>0761 120 120 00</li>
      <li>kzvbw.de</li>
      <li><h6>Tropeninstitut</h6></li>
      <li>06221 5622999</li>
      <li><h6>Giftinformationszentrum</h6></li>
      <li>0761 19240</li>
    </ul>
  </KontaktItem>
</div>
    </div>
  </section>
</template>

<script setup>
import SectionHeading from '../core/SectionHeading.vue';
import KontaktItem from './KontaktItem.vue';
</script>

<style scoped>
.kontakt-section {
  padding: var(--spacing-xxl) 0;
  background-color: var(--color-background);
  font-size: var(--font-size-base);
  font-weight: var(--font-weight-medium);
}

.kontakt-items-grid {
  color: var(--color-primary);
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: var(--spacing-xl);
  row-gap: var(--spacing-lg);
  max-width: 1100px;
  margin: 0 auto;
  padding-top: var(--spacing-lg);
}

h6 {
  padding-top: var(--spacing-sm);
  font-weight: var(--font-weight-regular);
}

li:not(:has(h6)) {
  color: var(--color-light-blue);
}

em {
  font-size: var(--font-size-sm);
}

@media (max-width: 992px) {
  .kontakt-items-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: var(--spacing-lg);
  }
}

@media (max-width: 450px) {
  .kontakt-items-grid {
    grid-template-columns: 1fr;
    gap: var(--spacing-md);
  }
}
</style>