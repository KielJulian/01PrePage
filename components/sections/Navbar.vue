<template>
  <header class="header" :class="{ 'scrolled': isScrolled }">
    <div class="navbar">
      <div class="logo">
        <h1>01PrePage</h1>
      </div>
      
      <nav class="nav-menu" :class="{ 'active': mobileMenuActive }">
        <ul class="nav-list">
          <li class="nav-item">
            <a href="#" class="nav-link">Home</a>
          </li>
          <li class="nav-item">
            <a href="#leistungen" class="nav-link">Leistungen</a>
          </li>
          <li class="nav-item">
            <a href="#praxis" class="nav-link">Praxis</a>
          </li>
          <li class="nav-item">
            <a href="#team" class="nav-link">Team</a>
          </li>
          <li class="nav-item">
            <a href="#kontakt" class="nav-link">Kontakt</a>
          </li>
        </ul>
      </nav>
      
      <div class="nav-right">
        <Button>Termin vereinbaren</Button>
        <div class="menu-toggle" @click="toggleMobileMenu">
          <div class="bar" :class="{ 'active': mobileMenuActive }"></div>
          <div class="bar" :class="{ 'active': mobileMenuActive }"></div>
          <div class="bar" :class="{ 'active': mobileMenuActive }"></div>
        </div>
      </div>
    </div>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
import Button from '../core/Button.vue';

const isScrolled = ref(false);
const mobileMenuActive = ref(false);

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50;
};

const toggleMobileMenu = () => {
  mobileMenuActive.value = !mobileMenuActive.value;
};

onMounted(() => {
  window.addEventListener('scroll', handleScroll);
});

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll);
});
</script>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 1000;
  transition: all 0.3s ease;
  background-color: transparent;
}

.header.scrolled {
  background-color: var(--color-white);
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: var(--navbar-width);
  margin: 0 auto;
  padding: var(--spacing-md) var(--spacing-lg);
  transition: all 0.3s ease;
}

.header.scrolled .navbar {
  padding: var(--spacing-sm) var(--spacing-lg);
}

.logo h1 {
  color: var(--color-primary);
  font-size: 1.8rem;
  margin: 0;
  transition: all 0.3s ease;
}

.header.scrolled .logo h1 {
  font-size: 1.5rem;
}

.nav-menu {
  transition: all 0.3s ease;
}

.nav-list {
  display: flex;
  list-style: none;
  gap: var(--spacing-md);
}

.nav-link {
  color: var(--color-primary);
  font-weight: 500;
  padding: var(--spacing-xs) 0;
  position: relative;
  transition: all 0.3s ease;
}

.nav-link::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 2px;
  background-color: var(--color-accent-yellow);
  transition: width 0.3s ease;
}

.nav-link:hover::after {
  width: 100%;
}

.nav-right {
  display: flex;
  align-items: center;
  gap: var(--spacing-md);
}

.menu-toggle {
  display: none;
  flex-direction: column;
  gap: 5px;
  cursor: pointer;
}

.bar {
  width: 25px;
  height: 3px;
  background-color: var(--color-primary);
  transition: all 0.3s ease;
}

.bar.active:nth-child(1) {
  transform: translateY(8px) rotate(45deg);
}

.bar.active:nth-child(2) {
  opacity: 0;
}

.bar.active:nth-child(3) {
  transform: translateY(-8px) rotate(-45deg);
}

@media (max-width: 900px) {
  .nav-menu {
    position: fixed;
    top: 0;
    right: -100%;
    width: 80%;
    max-width: 400px;
    height: 100vh;
    background-color: var(--color-white);
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    box-shadow: -2px 0 10px rgba(0, 0, 0, 0.1);
    transition: right 0.3s ease;
  }

  .nav-menu.active {
    right: 0;
  }

  .nav-list {
    flex-direction: column;
    text-align: center;
  }

  .nav-item {
    margin: var(--spacing-sm) 0;
  }

  .menu-toggle {
    display: flex;
  }
}
</style> 