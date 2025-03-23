<template>
  <div class="page-container">
    <SectionHeading 
      title="Impressum" 
      subtitle="Rechtliche Informationen über 01PrePage"
    />
    
    <div class="content-card">
      <h2>Angaben gemäß § 5 TMG</h2>
      <p>01PrePage GmbH<br>
      Musterstraße 123<br>
      12345 Musterstadt<br>
      Deutschland</p>

      <h3>Kontakt</h3>
      <p>Telefon: +49 (0) 123 456 7890<br>
      E-Mail: info@01prepage.de</p>

      <h3>Vertretungsberechtigte Geschäftsführer</h3>
      <p>Dr. Martina Weber, Dr. Thomas Müller</p>

      <h3>Registereintrag</h3>
      <p>Eintragung im Handelsregister.<br>
      Registergericht: Amtsgericht Musterstadt<br>
      Registernummer: HRB 12345</p>

      <h3>Umsatzsteuer-ID</h3>
      <p>Umsatzsteuer-Identifikationsnummer gemäß § 27 a Umsatzsteuergesetz:<br>
      DE 123456789</p>

      <h3>Ärztliche Berufsbezeichnung und berufsrechtliche Regelungen</h3>
      <p>Berufsbezeichnung: Arzt/Ärztin (verliehen in der Bundesrepublik Deutschland)<br>
      Zuständige Ärztekammer: Ärztekammer Musterstadt<br>
      Berufsrechtliche Regelungen: Berufsordnung für die Ärzte, einsehbar unter www.aerzteblatt.de</p>

      <h3>Verantwortlich für den Inhalt nach § 55 Abs. 2 RStV</h3>
      <p>Dr. Martina Weber<br>
      01PrePage GmbH<br>
      Musterstraße 123<br>
      12345 Musterstadt</p>

      <h3>Streitschlichtung</h3>
      <p>Die Europäische Kommission stellt eine Plattform zur Online-Streitbeilegung (OS) bereit: https://ec.europa.eu/consumers/odr.<br>
      Unsere E-Mail-Adresse finden Sie oben im Impressum. Wir sind nicht bereit oder verpflichtet, an Streitbeilegungsverfahren vor einer Verbraucherschlichtungsstelle teilzunehmen.</p>

      <h3>Haftung für Inhalte</h3>
      <p>Als Diensteanbieter sind wir gemäß § 7 Abs.1 TMG für eigene Inhalte auf diesen Seiten nach den allgemeinen Gesetzen verantwortlich. Nach §§ 8 bis 10 TMG sind wir als Diensteanbieter jedoch nicht verpflichtet, übermittelte oder gespeicherte fremde Informationen zu überwachen oder nach Umständen zu forschen, die auf eine rechtswidrige Tätigkeit hinweisen.</p>
      <p>Verpflichtungen zur Entfernung oder Sperrung der Nutzung von Informationen nach den allgemeinen Gesetzen bleiben hiervon unberührt. Eine diesbezügliche Haftung ist jedoch erst ab dem Zeitpunkt der Kenntnis einer konkreten Rechtsverletzung möglich. Bei Bekanntwerden von entsprechenden Rechtsverletzungen werden wir diese Inhalte umgehend entfernen.</p>
    </div>
  </div>
</template>

<script setup>
import SectionHeading from '~/components/core/SectionHeading.vue';

definePageMeta({
  layout: 'default'
})
</script>

<style scoped>
.page-container {
  padding: var(--spacing-xxl) 0;
  max-width: var(--content-width);
  margin: 0 auto;
  padding-left: var(--spacing-md);
  padding-right: var(--spacing-md);
}

.content-card {
  margin-bottom: var(--spacing-xl);
}

h2 {
  color: var(--color-primary);
  margin-bottom: var(--spacing-md);
  font-size: 1.5rem;
}

h3 {
  color: var(--color-primary);
  margin-top: var(--spacing-lg);
  margin-bottom: var(--spacing-sm);
  font-size: 1.2rem;
}

p {
  margin-bottom: var(--spacing-md);
  line-height: 1.6;
  color: #333;
}
</style> 