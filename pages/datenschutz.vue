<template>
  <div class="page-container">
    <SectionHeading 
      title="Datenschutzerklärung" 
      subtitle="Informationen zum Schutz Ihrer persönlichen Daten"
    />
    
    <div class="content-card">
      <h2>1. Datenschutz auf einen Blick</h2>
      <h3>Allgemeine Hinweise</h3>
      <p>Die folgenden Hinweise geben einen einfachen Überblick darüber, was mit Ihren personenbezogenen Daten passiert, wenn Sie diese Website besuchen. Personenbezogene Daten sind alle Daten, mit denen Sie persönlich identifiziert werden können. Ausführliche Informationen zum Thema Datenschutz entnehmen Sie unserer unter diesem Text aufgeführten Datenschutzerklärung.</p>

      <h3>Datenerfassung auf dieser Website</h3>
      <p><strong>Wer ist verantwortlich für die Datenerfassung auf dieser Website?</strong><br>
      Die Datenverarbeitung auf dieser Website erfolgt durch den Websitebetreiber. Dessen Kontaktdaten können Sie dem Impressum dieser Website entnehmen.</p>

      <p><strong>Wie erfassen wir Ihre Daten?</strong><br>
      Ihre Daten werden zum einen dadurch erhoben, dass Sie uns diese mitteilen. Hierbei kann es sich z. B. um Daten handeln, die Sie in ein Kontaktformular eingeben.</p>
      <p>Andere Daten werden automatisch oder nach Ihrer Einwilligung beim Besuch der Website durch unsere IT-Systeme erfasst. Das sind vor allem technische Daten (z. B. Internetbrowser, Betriebssystem oder Uhrzeit des Seitenaufrufs). Die Erfassung dieser Daten erfolgt automatisch, sobald Sie diese Website betreten.</p>

      <p><strong>Wofür nutzen wir Ihre Daten?</strong><br>
      Ein Teil der Daten wird erhoben, um eine fehlerfreie Bereitstellung der Website zu gewährleisten. Andere Daten können zur Analyse Ihres Nutzerverhaltens verwendet werden.</p>

      <p><strong>Welche Rechte haben Sie bezüglich Ihrer Daten?</strong><br>
      Sie haben jederzeit das Recht, unentgeltlich Auskunft über Herkunft, Empfänger und Zweck Ihrer gespeicherten personenbezogenen Daten zu erhalten. Sie haben außerdem ein Recht, die Berichtigung oder Löschung dieser Daten zu verlangen. Wenn Sie eine Einwilligung zur Datenverarbeitung erteilt haben, können Sie diese Einwilligung jederzeit für die Zukunft widerrufen. Außerdem haben Sie das Recht, unter bestimmten Umständen die Einschränkung der Verarbeitung Ihrer personenbezogenen Daten zu verlangen.</p>

      <h2>2. Allgemeine Hinweise und Pflichtinformationen</h2>
      <h3>Datenschutz</h3>
      <p>Die Betreiber dieser Seiten nehmen den Schutz Ihrer persönlichen Daten sehr ernst. Wir behandeln Ihre personenbezogenen Daten vertraulich und entsprechend der gesetzlichen Datenschutzvorschriften sowie dieser Datenschutzerklärung.</p>
      <p>Wenn Sie diese Website benutzen, werden verschiedene personenbezogene Daten erhoben. Personenbezogene Daten sind Daten, mit denen Sie persönlich identifiziert werden können. Die vorliegende Datenschutzerklärung erläutert, welche Daten wir erheben und wofür wir sie nutzen. Sie erläutert auch, wie und zu welchem Zweck das geschieht.</p>

      <h3>Hinweis zur verantwortlichen Stelle</h3>
      <p>Die verantwortliche Stelle für die Datenverarbeitung auf dieser Website ist:</p>
      <p>01PrePage GmbH<br>
      Dr. Martina Weber<br>
      Musterstraße 123<br>
      12345 Musterstadt</p>
      <p>Telefon: +49 (0) 123 456 7890<br>
      E-Mail: info@01prepage.de</p>

      <h3>Speicherdauer</h3>
      <p>Soweit innerhalb dieser Datenschutzerklärung keine speziellere Speicherdauer genannt wurde, verbleiben Ihre personenbezogenen Daten bei uns, bis der Zweck für die Datenverarbeitung entfällt. Wenn Sie ein berechtigtes Löschersuchen geltend machen oder eine Einwilligung zur Datenverarbeitung widerrufen, werden Ihre Daten gelöscht, sofern wir keine anderen rechtlich zulässigen Gründe für die Speicherung Ihrer personenbezogenen Daten haben (z. B. steuer- oder handelsrechtliche Aufbewahrungsfristen); im letztgenannten Fall erfolgt die Löschung nach Fortfall dieser Gründe.</p>

      <h3>Widerruf Ihrer Einwilligung zur Datenverarbeitung</h3>
      <p>Viele Datenverarbeitungsvorgänge sind nur mit Ihrer ausdrücklichen Einwilligung möglich. Sie können eine bereits erteilte Einwilligung jederzeit widerrufen. Die Rechtmäßigkeit der bis zum Widerruf erfolgten Datenverarbeitung bleibt vom Widerruf unberührt.</p>

      <h3>Beschwerderecht bei der zuständigen Aufsichtsbehörde</h3>
      <p>Im Falle von Verstößen gegen die DSGVO steht den Betroffenen ein Beschwerderecht bei einer Aufsichtsbehörde, insbesondere in dem Mitgliedstaat ihres gewöhnlichen Aufenthalts, ihres Arbeitsplatzes oder des Orts des mutmaßlichen Verstoßes zu. Das Beschwerderecht besteht unbeschadet anderweitiger verwaltungsrechtlicher oder gerichtlicher Rechtsbehelfe.</p>

      <h3>Recht auf Datenübertragbarkeit</h3>
      <p>Sie haben das Recht, Daten, die wir auf Grundlage Ihrer Einwilligung oder in Erfüllung eines Vertrags automatisiert verarbeiten, an sich oder an einen Dritten in einem gängigen, maschinenlesbaren Format aushändigen zu lassen. Sofern Sie die direkte Übertragung der Daten an einen anderen Verantwortlichen verlangen, erfolgt dies nur, soweit es technisch machbar ist.</p>
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
  max-width: var(--content-width);
  display: flex;
  flex-direction: row;
  align-items: start;
  justify-content: space-between;
  gap: var(--spacing-4xl);
  margin: 0 auto;
  padding-left: var(--spacing-md);
  padding-right: var(--spacing-md);
  margin-top: var(--spacing-4xl);
  margin-bottom: var(--spacing-xl);
}

.content-card {
  max-width: var(--content-width-text);
}

h2 {
  color: var(--color-primary);
  margin-bottom: var(--spacing-md);
  margin-top: var(--spacing-lg);
  font-size: 1.5rem;
}

h2:first-child {
  margin: 0;
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

strong {
  color: var(--color-primary);
}
</style> 