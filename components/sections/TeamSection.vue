<template>
  <section id="team" class="team-section">
    <div class="container">
      <SectionHeading 
        title="Unser Team" 
        subtitle="Lernen Sie unser erfahrenes Team von Gesundheitsexperten kennen"
      />
      
      <div class="team-grid">
        <TeamItem 
          v-for="(member, index) in teamMembers" 
          :key="index"
          :image="member.image"
          :name="member.name"
          :position="member.position"
          :description="member.description"
          :specialties="member.specialties"
        />
      </div>
    </div>
  </section>
</template>

<script setup>
import SectionHeading from '../core/SectionHeading.vue';
import TeamItem from './TeamItem.vue';

const teamMembers = [
  {
    name: 'Dr. Martina Weber',
    position: 'Leitende Ärztin',
    // description: 'Dr. Weber bringt über 15 Jahre Erfahrung in der allgemeinen Medizin mit und leitet unser Ärzteteam mit Expertise und Einfühlungsvermögen.',
    // specialties: ['Allgemeinmedizin', 'Präventive Medizin'],
    image: '/img/team/Dr-Martina-Weber.jpg'
  },
  {
    name: 'Dr. Thomas Merano',
    position: 'Kardiologe',
    // description: 'Als Spezialist für Herzgesundheit bringt Dr. Müller umfassende Erfahrung in der Diagnose und Behandlung kardiovaskulärer Erkrankungen mit.',
    // specialties: ['Kardiologie', 'Innere Medizin'],
    image: '/img/team/Dr-Thomas-Müller.jpg'
  },
  {
    name: 'Dr. Sophie Becker',
    position: 'Dermatologin',
    // description: 'Dr. Becker ist auf Hautgesundheit und ästhetische Dermatologie spezialisiert und bietet moderne Behandlungsmethoden für verschiedene Hauterkrankungen.',
    // specialties: ['Dermatologie', 'Ästhetische Medizin'],
    image: '/img/team/Dr-Sophie-Becker.jpg'
  },
  {
    name: 'Marion Schmidt',
    position: 'Medizinische Fachangestellte',
    // description: 'Marion kümmert sich um administrative Aufgaben und sorgt für einen reibungslosen Praxisablauf. Sie ist oft Ihre erste Ansprechpartnerin in unserer Praxis.',
    // specialties: ['Patientenbetreuung', 'Organisation'],
    image: '/img/team/Marion-Schmidt.jpg'
  },
  {
    name: 'Maria Garcia',
    position: 'Ernährungsberaterin',
    // description: 'Maria unterstützt unsere Patienten mit personalisierten Ernährungsplänen und berät zu gesunder Lebensweise.',
    // specialties: ['Ernährungsberatung', 'Diätetik'],
    image: '/img/team/maria-garcia.jpg'
  },
  {
    name: 'Dr. Albert Dera',
    position: 'Neurologe',
    // description: 'Dr. Dera ist spezialisiert auf die Diagnose und Behandlung von neurologischen Erkrankungen mit besonderem Fokus auf nicht-invasive Therapiemethoden.',
    // specialties: ['Neurologie', 'Schmerztherapie'],
    image: '/img/team/albert-dera.jpg'
  },
  {
    name: 'Polova Hans',
    position: 'Physiotherapeut',
    // description: 'Polova verfügt über umfangreiche Erfahrung in der Rehabilitation und unterstützt unsere Patienten bei der Wiederherstellung ihrer Mobilität.',
    // specialties: ['Physiotherapie', 'Sportrehabilitation'],
    image: '/img/team/polova-hans.jpg'
  },
  {
    name: 'Jurica Mensen',
    position: 'Psychotherapeut',
    // description: 'Jurica bietet psychologische Unterstützung und Therapie für Patienten mit verschiedenen psychischen Herausforderungen.',
    // specialties: ['Psychotherapie', 'Stressbewältigung'],
    image: '/img/team/jurica-mensen.jpg'
  },
  {
    name: 'Darshan Patel',
    position: 'Orthopäde',
    // description: 'Dr. Patel ist Experte für Erkrankungen des Bewegungsapparates und berät zu konservativen und operativen Behandlungsmöglichkeiten.',
    // specialties: ['Orthopädie', 'Sportmedizin'],
    image: '/img/team/darshan-patel.jpg'
  }
];
</script>

<style scoped>
.team-section {
  padding: var(--spacing-xxl) 0;
  background-color: var(--color-background);
}

.team-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: var(--spacing-lg);
}

@media (max-width: 1200px) {
  .team-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

@media (max-width: 992px) {
  .team-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 576px) {
  .team-grid {
    grid-template-columns: repeat(1, 1fr);
  }
}
</style> 