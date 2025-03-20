<template>
  <section id="kontakt" class="kontakt-section">
    <div class="container">
      <SectionHeading 
        title="Kontakt" 
        subtitle="Wir sind für Sie da. Nehmen Sie Kontakt mit uns auf."
      />
      
      <div class="kontakt-items-grid">
        <KontaktItem title="Sichere Datenübertragung">
          <template #icon>
            <span>✓</span>
          </template>
          <p>Heureka überträgt Praxisdaten sicher verschlüsselt aus deinem System an die Anwendung.</p>
        </KontaktItem>
        
        <KontaktItem title="Kein Speichern deiner Daten">
          <template #icon>
            <span>✓</span>
          </template>
          <p>Heureka liest deine Praxisdaten nicht mit und speichert diese auch nicht. Deine Daten bleiben in deinem PIS.</p>
        </KontaktItem>
        
        <KontaktItem title="Entscheidungsfreiheit - 100%">
          <template #icon>
            <span>✓</span>
          </template>
          <p>Heureka lässt dir offen, wohin du welche Daten teilen willst - immer mit dem notwendigen Patienteneinverständnis.</p>
        </KontaktItem>
        
        <KontaktItem title="Datenschutzkonform">
          <template #icon>
            <span>✓</span>
          </template>
          <p>Heureka, sowie die eingebundenen Anwendungen, halten sich an die Vorgaben gemäss neuem Schweizer DSG.</p>
        </KontaktItem>
        
        <KontaktItem title="Volle Transparenz der Datenabfragen">
          <template #icon>
            <span>✓</span>
          </template>
          <p>Heureka ermöglicht dir jederzeit jegliche Zugriffe deiner Anwendungen einzusehen.</p>
        </KontaktItem>
        
        <KontaktItem title="Von Experten geprüft und empfohlen">
          <template #icon>
            <span>✓</span>
          </template>
          <p>Heureka wird regelmässig punkto Sicherheit und Datenschutz geprüft und bindet die Experten aktiv mit ein.</p>
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
}

.kontakt-items-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: var(--spacing-xl);
  row-gap: var(--spacing-lg);
  max-width: 1100px;
  margin: 0 auto;
  padding-top: var(--spacing-lg);
}

@media (max-width: 992px) {
  .kontakt-items-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: var(--spacing-lg);
  }
}

@media (max-width: 576px) {
  .kontakt-items-grid {
    grid-template-columns: 1fr;
    gap: var(--spacing-md);
  }
}
</style>