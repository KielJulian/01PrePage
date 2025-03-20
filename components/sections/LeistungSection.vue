<template>
  <section id="leistungen" class="leistung-section">
    <div class="container">
      <SectionHeading 
        title="Unsere Leistungen" 
        subtitle="Wir bieten ein breites Spektrum an medizinischen Dienstleistungen für Ihre Gesundheit"
      />
      
      <div class="leistung-categories">
        <!-- Diagnostische Untersuchungen -->
        <div class="leistung-category">
          <h2 class="category-title">Diagnostische Untersuchungen</h2>
          <div class="leistung-grid">
            <LeistungItem 
              v-for="leistung in diagnosticServices" 
              :key="leistung.title"
              :title="leistung.title"
              :description="leistung.description"
            />
          </div>
        </div>

        <div class="category-divider"></div>

        <!-- Vorsorgeuntersuchungen -->
        <div class="leistung-category">
          <h2 class="category-title">Vorsorgeuntersuchungen</h2>
          <div class="leistung-grid">
            <LeistungItem 
              v-for="leistung in preventiveServices" 
              :key="leistung.title"
              :title="leistung.title"
              :description="leistung.description"
            />
          </div>
        </div>

        <div class="category-divider"></div>

        <!-- Individuelle Gesundheitsleistungen -->
        <div class="leistung-category">
          <h2 class="category-title">Individuelle Gesundheitsleistungen (IGeL)</h2>
          <div class="leistung-grid">
            <LeistungItem 
              v-for="leistung in individualServices" 
              :key="leistung.title"
              :title="leistung.title"
              :description="leistung.description"
            />
          </div>
        </div>

        <div class="category-divider"></div>

        <!-- Naturheilverfahren -->
        <div class="leistung-category">
          <h2 class="category-title">Naturheilverfahren</h2>
          <div class="leistung-grid">
            <LeistungItem 
              v-for="leistung in naturalHealingServices" 
              :key="leistung.title"
              :title="leistung.title"
              :description="leistung.description"
            />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import SectionHeading from '../core/SectionHeading.vue';
import LeistungItem from './LeistungItem.vue';

const diagnosticServices = [
  {
    title: 'Herz-Kreislauf-Untersuchungen',
    description: 'EKG, Belastungs-EKG'
  },
  {
    title: 'Langzeit-Blutdruckmessung',
    description: 'Kontinuierliche Überwachung des Blutdrucks über einen längeren Zeitraum'
  },
  {
    title: 'Schnelltest',
    description: 'Schnelltests auf Herzinfarkt, Lungenembolie, Beinvenenthrombose'
  },
  {
    title: 'Lungenfunktionsdiagnostik',
    description: 'Umfassende Untersuchung der Lungenfunktion'
  },
  {
    title: 'Ultraschall',
    description: 'Ultraschalluntersuchungen verschiedener Organe'
  },
  {
    title: 'Laboruntersuchungen',
    description: 'Umfassende Blut- und Gewebeanalysen'
  }
];

const preventiveServices = [
  {
    title: 'Stuhltest zur Tumorerkennung',
    description: 'Früherkennungstest für Darmkrebs'
  },
  {
    title: 'Gesundheitsuntersuchung (18-35 Jahre)',
    description: 'Vorsorgeuntersuchung für junge Erwachsene'
  },
  {
    title: 'Gesundheitsuntersuchung (ab 35 Jahre)',
    description: 'Umfassende Vorsorgeuntersuchung für Erwachsene'
  },
  {
    title: 'Krebsvorsorge Männer',
    description: 'Spezielle Vorsorgeuntersuchung für Männer ab 45 Jahren'
  }
];

const individualServices = [
  {
    title: 'Reiseimpfungen',
    description: 'Impfberatung und -durchführung für Auslandsreisen'
  },
  {
    title: 'Sport-Tauch-Tauglichkeitsuntersuchung',
    description: 'Umfassende Untersuchung zur Feststellung der Tauglichkeit für Tauchsport'
  }
];

const naturalHealingServices = [
  {
    title: 'Phytotherapie',
    description: 'Behandlung mit pflanzlichen Wirkstoffen'
  },
  {
    title: 'Bewegungstherapie',
    description: 'Therapie durch gezielte körperliche Übungen'
  },
  {
    title: 'Diätetik',
    description: 'Beratung zu Ernährung und speziellen Diäten'
  },
  {
    title: 'Ordnungstherapie',
    description: 'Ansätze zur Verbesserung der Lebensweise'
  },
  {
    title: 'Pflanzenheilkunde',
    description: 'Nutzung der Heilkraft von Pflanzen'
  },
  {
    title: 'Akupunktur',
    description: 'Traditionelle chinesische Heilmethode'
  },
  {
    title: 'Triggerpunktbehandlung',
    description: 'Gezielte Behandlung von Schmerzpunkten'
  },
  {
    title: 'Homöopathie',
    description: 'Alternativmedizinische Behandlungsmethode'
  },
  {
    title: 'Neuraltherapie nach Huneke',
    description: 'Injektionstherapie zur Behandlung von Schmerzen'
  },
  {
    title: 'Schröpfen',
    description: 'Traditionelles Verfahren der Naturheilkunde'
  },
  {
    title: 'Eigenbluttherapie',
    description: 'Behandlung zur Steigerung der körpereigenen Abwehr'
  }
];
</script>

<style scoped>
.leistung-section {
  padding: var(--spacing-xxl) 0;
  background-color: var(--color-background);
}

.leistung-categories {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-xl);
}

.category-title {
  color: var(--color-primary);
  margin-bottom: var(--spacing-md);
  font-size: 1.8rem;
}

.leistung-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: var(--spacing-lg);
}

.category-divider {
  height: 1px;
  background-color: var(--color-border, #e0e0e0);
  margin: var(--spacing-md) 0;
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
  
  .category-title {
    font-size: 1.5rem;
  }
}
</style> 