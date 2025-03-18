<template>
  <section id="leistungen" class="leistung-section">
    <div class="container">
      <SectionHeading 
        title="Unsere Leistungen" 
        subtitle="Wir bieten ein breites Spektrum an medizinischen Dienstleistungen für Ihre Gesundheit"
      />
      
      <div class="leistung-grid">
        <LeistungItem 
          v-for="(leistung, index) in leistungen" 
          :key="index"
          :icon="leistung.icon"
          :iconBgColor="leistung.iconBgColor"
          :title="leistung.title"
          :description="leistung.description"
        />
      </div>
    </div>
  </section>
</template>

<script setup>
import SectionHeading from '../core/SectionHeading.vue';
import LeistungItem from './LeistungItem.vue';

const leistungen = [
  {
    title: 'Allgemeine Medizin',
    description: 'Umfassende medizinische Versorgung für die ganze Familie. Unser Fokus liegt auf präventiver Gesundheitsvorsorge und individueller Beratung.',
    iconBgColor: 'var(--color-highlight-mint)'
  },
  {
    title: 'Kardiologie',
    description: 'Spezialisten für Herzgesundheit und kardiovaskuläre Erkrankungen. Modernste Diagnoseverfahren und personalisierte Behandlungspläne.',
    iconBgColor: 'var(--color-highlight-pink)'
  },
  {
    title: 'Dermatologie',
    description: 'Hautgesundheit und ästhetische Dermatologie. Wir behandeln verschiedene Hauterkrankungen und bieten kosmetische Dermatologie an.',
    iconBgColor: 'var(--color-highlight-purple)'
  },
  {
    title: 'Orthopädie',
    description: 'Behandlung von Erkrankungen und Verletzungen des Bewegungsapparates. Moderne Techniken zur Schmerzlinderung und Rehabilitation.',
    iconBgColor: 'var(--color-accent-yellow)'
  },
  {
    title: 'Pädiatrie',
    description: 'Spezialisierte medizinische Versorgung für Kinder. Wir schaffen eine kinderfreundliche Umgebung für eine angenehme Behandlung.',
    iconBgColor: 'var(--color-highlight-mint)'
  },
  {
    title: 'Psychologie',
    description: 'Psychologische Beratung und Therapie für mentale Gesundheit. Vertrauliche und unterstützende Umgebung für alle Altersgruppen.',
    iconBgColor: 'var(--color-accent-grey)'
  }
];
</script>

<style scoped>
.leistung-section {
  padding: var(--spacing-xxl) 0;
  background-color: var(--color-background);
}

.leistung-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: var(--spacing-lg);
}

@media (max-width: 992px) {
  .leistung-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 576px) {
  .leistung-grid {
    grid-template-columns: 1fr;
  }
}
</style> 