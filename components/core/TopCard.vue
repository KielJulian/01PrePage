<template>
  <div class="container">
    <div class="top-card">
      <div class="hero-section-text">
        <h1
        >Vorschau-Seite</h1>
        <p>Willkommen auf der Vorschau-Seite! Design, Inhalte 
          und Funktionen können individuell 
          angepasst werden – teilen Sie mir gerne Ihre Wünsche mit.</p>
          <Button @click="scrollToLeistungen">Zu den Leistungen</Button>
      </div>
      <div class="hero-section-item">
        <Hero4Pictures />
      </div>
    </div>
    <HeroTeamPreview />
  </div>
</template>

<script setup>
import Button from '~/components/core/Button.vue';
import Hero4Pictures from '~/components/HeroItems/Hero4Pictures.vue';
import HeroTeamPreview from '~/components/HeroItems/HeroTeamPreview.vue';

const scrollToLeistungen = () => {
  const leistungSection = document.querySelector('.leistung-section');
  if (leistungSection) {
    const rect = leistungSection.getBoundingClientRect();
    const scrollTop = window.pageYOffset || document.documentElement.scrollTop;
    const targetPosition = scrollTop + rect.top - 100; // 100px offset
    window.scrollTo({
      top: targetPosition,
      behavior: 'smooth'
    });
  }
};
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-around;
  height: calc(100svh - (90px + 2 * 4rem));
  margin-top: 4rem;
  margin-bottom: 4rem;
}

h1 {
  color: var(--color-accent-green);
}

p {
  font-weight: var(--font-weight-regular);
  font-size: var(--font-size-xl);
}

.top-card {
  color: var(--color-primary);
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  gap: var(--spacing-xl);
  width: 100%;
}

.hero-section-text {
  align-self: flex-start;
  gap: var(--spacing-md);
  display: flex;
  flex-direction: column;
  align-self: center;
  align-items: flex-start;
  width: 50%;
}

.hero-section-item {
  width: 50%;
}
@media (max-width: 768px) {
  .container {
   align-items: flex-start;
   align-items: center;
   height: calc(100svh - (80px));
   margin: 0;
  }

.top-card {
  flex-direction: column;
}

  .hero-section-text {
    align-items: center;
    padding: 0;
    width: 100%;
    text-align: center;
  }

  h1 {
    text-align: center;
  }
  .hero-section-item {
    display: none;
  }
}
</style> 
