<template>
  <section id="leistungen" class="leistung-section">
    <div class="container">
      <SectionHeading 
        title="Unsere Leistungen" 
        subtitle="Wir bieten ein breites Spektrum an medizinischen Dienstleistungen für Ihre Gesundheit"
      />
      
      <div class="tag-filter">
        <span class="tag-label">Nach Bereich filtern</span>
        <div class="tag-buttons">
          <Tag 
            v-for="tag in availableTags" 
            :key="tag"
            :text="tag"
            :isActive="selectedTags.includes(tag)"
            @click="toggleTag(tag)"
          />
        </div>
        <button v-if="selectedTags.length > 0" class="clear-filter" @click="clearTags">
          Filter zurücksetzen
        </button>
      </div>
      
      <!-- Show filtered items when tags are selected -->
      <div v-if="selectedTags.length > 0" class="filtered-items">
        <div class="leistung-grid">
          <LeistungItem 
            v-for="leistung in filteredServices" 
            :key="leistung.title"
            :title="leistung.title"
            :description="leistung.description"
            :tags="leistung.tags"
          />
        </div>
      </div>
      
      <!-- Show categories when no tags are selected -->
      <div v-else class="leistung-categories">
        <!-- Diagnostische Untersuchungen -->
        <div class="collapsible-category">
          <div class="category-header" @click="toggleCategory('diagnostics')">
            <h3 class="category-title">Diagnostische Untersuchungen</h3>
          </div>
          <div class="category-content" v-show="openCategories.diagnostics">
            <div class="leistung-grid">
              <LeistungItem 
                v-for="leistung in diagnosticServices" 
                :key="leistung.title"
                :title="leistung.title"
                :description="leistung.description"
                :tags="leistung.tags"
              />
            </div>
          </div>
        </div>

        <div class="category-divider"></div>

        <!-- Vorsorgeuntersuchungen -->
        <div class="collapsible-category">
          <div class="category-header" @click="toggleCategory('preventive')">
            <h3 class="category-title">Vorsorgeuntersuchungen</h3>
          </div>
          <div class="category-content" v-show="openCategories.preventive">
            <div class="leistung-grid">
              <LeistungItem 
                v-for="leistung in preventiveServices" 
                :key="leistung.title"
                :title="leistung.title"
                :description="leistung.description"
                :tags="leistung.tags"
              />
            </div>
          </div>
        </div>

        <div class="category-divider"></div>

        <!-- Individuelle Gesundheitsleistungen -->
        <div class="collapsible-category">
          <div class="category-header" @click="toggleCategory('individual')">
            <h3 class="category-title">Individuelle Gesundheitsleistungen (IGeL)</h3>
          </div>
          <div class="category-content" v-show="openCategories.individual">
            <div class="leistung-grid">
              <LeistungItem 
                v-for="leistung in individualServices" 
                :key="leistung.title"
                :title="leistung.title"
                :description="leistung.description"
                :tags="leistung.tags"
              />
            </div>
          </div>
        </div>

        <div class="category-divider"></div>

        <!-- Naturheilverfahren -->
        <div class="collapsible-category">
          <div class="category-header" @click="toggleCategory('naturalHealing')">
            <h3 class="category-title">Naturheilverfahren</h3>
          </div>
          <div class="category-content" v-show="openCategories.naturalHealing">
            <div class="leistung-grid">
              <LeistungItem 
                v-for="leistung in naturalHealingServices" 
                :key="leistung.title"
                :title="leistung.title"
                :description="leistung.description"
                :tags="leistung.tags"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed, onMounted } from 'vue';
import SectionHeading from '../core/SectionHeading.vue';
import LeistungItem from './LeistungItem.vue';
import Tag from '../core/Tag.vue';

const selectedTags = ref([]);
const openCategories = ref({
  diagnostics: true,
  preventive: true,
  individual: true,
  naturalHealing: true
});

onMounted(() => {
  const isMobile = window.innerWidth < 768; // Common breakpoint for mobile
  if (isMobile) {
    openCategories.value = {
      diagnostics: false,
      preventive: false,
      individual: false,
      naturalHealing: false
    };
  }
});

const toggleCategory = (category) => {
  openCategories.value[category] = !openCategories.value[category];
};

const diagnosticServices = [
  {
    title: 'Herz-Kreislauf-Untersuchungen',
    description: 'EKG, Belastungs-EKG',
    tags: ['Diagnostik', 'HerzKreislauf']
  },
  {
    title: 'Langzeit-Blutdruckmessung',
    description: 'Kontinuierliche Überwachung des Blutdrucks über einen längeren Zeitraum',
    tags: ['Diagnostik', 'HerzKreislauf']
  },
  {
    title: 'Schnelltest',
    description: 'Schnelltests auf Herzinfarkt, Lungenembolie, Beinvenenthrombose',
    tags: ['Diagnostik', 'HerzKreislauf']
  },
  {
    title: 'Lungenfunktionsdiagnostik',
    description: 'Umfassende Untersuchung der Lungenfunktion',
    tags: ['Diagnostik', 'Lunge']
  },
  {
    title: 'Ultraschall',
    description: 'Ultraschalluntersuchungen verschiedener Organe',
    tags: ['Diagnostik']
  },
  {
    title: 'Laboruntersuchungen',
    description: 'Umfassende Blut- und Gewebeanalysen',
    tags: ['Diagnostik']
  }
];

const preventiveServices = [
  {
    title: 'Stuhltest zur Tumorerkennung',
    description: 'Früherkennungstest für Darmkrebs',
    tags: ['Vorsorge', 'Krebs']
  },
  {
    title: 'Gesundheitsuntersuchung (18-35 Jahre)',
    description: 'Vorsorgeuntersuchung für junge Erwachsene',
    tags: ['Vorsorge']
  },
  {
    title: 'Gesundheitsuntersuchung (ab 35 Jahre)',
    description: 'Umfassende Vorsorgeuntersuchung für Erwachsene',
    tags: ['Vorsorge']
  },
  {
    title: 'Krebsvorsorge Männer',
    description: 'Spezielle Vorsorgeuntersuchung für Männer ab 45 Jahren',
    tags: ['Vorsorge', 'Krebs']
  }
];

const individualServices = [
  {
    title: 'Reiseimpfungen',
    description: 'Impfberatung und -durchführung für Auslandsreisen',
    tags: ['IGeL', 'Immunsystem']
  },
  {
    title: 'Sport-Tauch-Tauglichkeitsuntersuchung',
    description: 'Umfassende Untersuchung zur Feststellung der Tauglichkeit für Tauchsport',
    tags: ['IGeL']
  }
];

const naturalHealingServices = [
  {
    title: 'Phytotherapie',
    description: 'Behandlung mit pflanzlichen Wirkstoffen',
    tags: ['Naturheilkunde']
  },
  {
    title: 'Bewegungstherapie',
    description: 'Therapie durch gezielte körperliche Übungen',
    tags: ['Naturheilkunde']
  },
  {
    title: 'Diätetik',
    description: 'Beratung zu Ernährung und speziellen Diäten',
    tags: ['Naturheilkunde', 'Ernährung']
  },
  {
    title: 'Ordnungstherapie',
    description: 'Ansätze zur Verbesserung der Lebensweise',
    tags: ['Naturheilkunde']
  },
  {
    title: 'Pflanzenheilkunde',
    description: 'Nutzung der Heilkraft von Pflanzen',
    tags: ['Naturheilkunde']
  },
  {
    title: 'Akupunktur',
    description: 'Traditionelle chinesische Heilmethode',
    tags: ['Naturheilkunde', 'Schmerztherapie']
  },
  {
    title: 'Triggerpunktbehandlung',
    description: 'Gezielte Behandlung von Schmerzpunkten',
    tags: ['Naturheilkunde', 'Schmerztherapie']
  },
  {
    title: 'Homöopathie',
    description: 'Alternativmedizinische Behandlungsmethode',
    tags: ['Naturheilkunde']
  },
  {
    title: 'Neuraltherapie nach Huneke',
    description: 'Injektionstherapie zur Behandlung von Schmerzen',
    tags: ['Naturheilkunde', 'Schmerztherapie']
  },
  {
    title: 'Schröpfen',
    description: 'Traditionelles Verfahren der Naturheilkunde',
    tags: ['Naturheilkunde', 'Schmerztherapie']
  },
  {
    title: 'Eigenbluttherapie',
    description: 'Behandlung zur Steigerung der körpereigenen Abwehr',
    tags: ['Naturheilkunde', 'Immunsystem']
  }
];

// Combine all services
const allServices = computed(() => [
  ...diagnosticServices,
  ...preventiveServices,
  ...individualServices,
  ...naturalHealingServices
]);

// Extract unique tags
const availableTags = computed(() => {
  const tagSet = new Set();
  allServices.value.forEach(service => {
    service.tags.forEach(tag => tagSet.add(tag));
  });
  return Array.from(tagSet).sort();
});

// Filter services based on selected tags
const filteredServices = computed(() => {
  if (selectedTags.value.length === 0) return allServices.value;
  
  return allServices.value.filter(service => 
    selectedTags.value.some(tag => service.tags.includes(tag))
  );
});

// Toggle tag selection
const toggleTag = (tag) => {
  if (selectedTags.value.includes(tag)) {
    selectedTags.value = selectedTags.value.filter(t => t !== tag);
  } else {
    selectedTags.value.push(tag);
  }
};

// Clear all selected tags
const clearTags = () => {
  selectedTags.value = [];
};
</script>

<style scoped>
h3 {
  font-size: var(--font-size-xs);
}

.leistung-section {
  padding: var(--spacing-xxl) 0;
  background-color: var(--color-background);
  min-height: 80vh;
}

.tag-filter {
  margin-bottom: var(--spacing-lg);
  display: flex;
  flex-direction: column;
  gap: var(--spacing-sm);
}

.tag-label {
  font-weight: 600;
  color: var(--color-primary);
  margin-bottom: var(--spacing-xs);
}

.tag-buttons {
  display: flex;
  flex-wrap: wrap;
  gap: var(--spacing-xs);
}

.clear-filter {
  padding: 6px 12px;
  border-radius: var(--radius-button);
  background-color: var(--color-background-alt, #f5f5f5);
  border: 1px solid var(--color-border, #e0e0e0);
  color: var(--color-text, #555);
  cursor: pointer;
  font-size: var(--font-size-sm);
  align-self: flex-start;
}

.clear-filter:hover {
  background-color: #e8e8e8;
}

.filtered-items {
  margin-top: var(--spacing-md);
}

.leistung-categories {
  display: flex;
  flex-direction: column;
}

.category-divider {
  height: 1px;
  margin: var(--spacing-md) 0;
}

.collapsible-category {
  overflow: hidden;
}

.category-header {
  display: flex;
  justify-content: start;
  align-items: center;
  cursor: pointer;
  padding-bottom: var(--spacing-md);
}

.category-title {
  color: var(--color-primary);
  margin-bottom: 0;
  font-size: 1.8rem;
}

.expand-icon {
  font-size: 1.5rem;
  font-weight: bold;
  color: var(--color-primary);
}

.category-content {
  background-color: var(--color-background);
  transition: all 0.3s ease;
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
  
  .tag-buttons {
    gap: 8px;
  }
  
  .tag-button {
    padding: 5px 10px;
    font-size: 0.8rem;
  }
  
  .category-title {
    font-size: 1.6rem;
  }
}

@media (max-width: 576px) {
  .leistung-grid {
    grid-template-columns: 1fr;
  }
  
  .category-title {
    font-size: 1.3rem;
  }
  
  .tag-buttons {
    flex-direction: row;
    flex-wrap: wrap;
  }
  
  .expand-icon {
    font-size: 1.2rem;
  }
}
</style> 