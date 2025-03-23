<template>
  <footer class="footer">
    <div class="footer-content">
      <div class="footer-logo">
        <h2>01PrePage</h2>
        <p>Ihr Spezialist für medizinische Versorgung</p>
      </div>
           
      <div class="footer-legal">
        <ul>
          <li><NuxtLink to="/impressum">Impressum</NuxtLink></li>
          <li><NuxtLink to="/datenschutz">Datenschutz</NuxtLink></li>
        </ul>
      </div>
    </div>

  </footer>
</template>

<style scoped>
.footer {
  width: var(--content-width);
  margin: 0 auto;
  padding: 0 var(--spacing-md);
}

.footer-content {
  padding: var(--spacing-xxl) 0;
  border-top: 1px solid var(--color-card-boarder);
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}

.footer-logo h2 {
  font-size: 1.8rem;
  margin-bottom: var(--spacing-xs);
}

.footer-logo p {
  opacity: 0.8;
}

.footer-legal ul {
  display: flex;
  flex-direction: row;
  gap: var(--spacing-md);
}

@media (max-width: 768px) {
  .footer-content {
    grid-template-columns: 1fr;
    gap: var(--spacing-lg);
    text-align: center;
  }
  
}
</style> 