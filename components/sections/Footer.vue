<template>
  <footer class="footer">
    <div class="footer-content">
      <div class="footer-logo">
        <h2>01PrePage</h2>
        <p>Ihr Spezialist für medizinische Versorgung</p>
      </div>
      
      <div class="footer-links">
        <h3>Links</h3>
        <ul>
          <li><a href="#leistungen">Leistungen</a></li>
          <li><a href="#praxis">Praxis</a></li>
          <li><a href="#team">Team</a></li>
          <li><a href="#kontakt">Kontakt</a></li>
        </ul>
      </div>
      
      <div class="footer-legal">
        <h3>Rechtliches</h3>
        <ul>
          <li><NuxtLink to="/impressum">Impressum</NuxtLink></li>
          <li><NuxtLink to="/datenschutz">Datenschutz</NuxtLink></li>
        </ul>
      </div>
    </div>
    
    <div class="footer-bottom">
      <p>&copy; {{ new Date().getFullYear() }} 01PrePage. Alle Rechte vorbehalten.</p>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  background-color: var(--color-primary);
  color: var(--color-white);
  padding: var(--spacing-xl) 0 var(--spacing-md);
}

.footer-content {
  max-width: var(--content-width);
  margin: 0 auto;
  display: grid;
  grid-template-columns: 2fr 1fr 1fr;
  gap: var(--spacing-xl);
  padding: 0 var(--spacing-md) var(--spacing-lg);
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.footer-logo h2 {
  font-size: 1.8rem;
  margin-bottom: var(--spacing-xs);
}

.footer-logo p {
  opacity: 0.8;
}

.footer-links h3,
.footer-legal h3 {
  font-size: 1.2rem;
  margin-bottom: var(--spacing-md);
  position: relative;
}

.footer-links h3::after,
.footer-legal h3::after {
  content: '';
  position: absolute;
  bottom: -8px;
  left: 0;
  width: 40px;
  height: 2px;
  background-color: var(--color-accent-yellow);
}

.footer-links ul,
.footer-legal ul {
  list-style: none;
}

.footer-links li,
.footer-legal li {
  margin-bottom: var(--spacing-xs);
}

.footer-links a,
.footer-legal a {
  color: var(--color-white);
  opacity: 0.8;
  transition: opacity 0.3s ease;
}

.footer-links a:hover,
.footer-legal a:hover {
  opacity: 1;
}

.footer-bottom {
  max-width: var(--content-width);
  margin: 0 auto;
  text-align: center;
  padding: var(--spacing-md);
  font-size: 0.9rem;
  opacity: 0.6;
}

@media (max-width: 768px) {
  .footer-content {
    grid-template-columns: 1fr;
    gap: var(--spacing-lg);
    text-align: center;
  }
  
  .footer-links h3::after,
  .footer-legal h3::after {
    left: 50%;
    transform: translateX(-50%);
  }
}
</style> 