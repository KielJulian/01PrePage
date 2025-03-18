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
  margin-top: var(--spacing-lg);
  transition: all 0.3s ease;
  background-color: transparent;
  box-sizing: border-box;
}

.header.scrolled {
  background-color: transparent;
  margin-top: var(--spacing-sm);
  width: calc(100% - var(--spacing-3xl) * 2);
  left: var(--spacing-3xl);
  right: var(--spacing-3xl);
  margin-left: 0;
  margin-right: 0;
}

.navbar {
  will-change: transform;
  transition: 
    border-width 0.2s ease,
    border-radius 0.2s ease 0.05s; 
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: var(--navbar-width);
  width: 100%;
  margin: 0 auto;
  padding: var(--spacing-md) var(--spacing-lg);
  box-sizing: border-box;
}

.header.scrolled .navbar {
  will-change: transform;
  transition: 
    border-radius 0.2s ease,    /* Radius changes first */
    border-width 0.2s ease 0.05s;
  padding: var(--spacing-sm) var(--spacing-lg);
  background-color: rgba(255, 255, 255, 0.85);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  border-radius: 32px;
  border: 1px solid var(--color-card-boarder);
  box-shadow: 
    rgba(0, 0, 0, 0.07) 0px 0.60219px 0.60219px -1.25px,
    rgba(0, 0, 0, 0.063) 0px 2.28853px 2.28853px -2.5px,
    rgba(0, 0, 0, 0.024) 0px 10px 10px -3.75px;
  margin: 0 auto;
  width: 100%;
  max-width: 100%;
}

/* For screens smaller than the max navbar width plus margins */
@media (max-width: calc(var(--navbar-width) + var(--spacing-3xl) * 2)) {
  .header.scrolled {
    width: calc(100% - var(--spacing-lg) * 2);
    left: var(--spacing-lg);
    right: var(--spacing-lg);
  }
  
  .header.scrolled .navbar {
    padding-left: var(--spacing-sm);
    padding-right: var(--spacing-sm);
  }
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
  .header.scrolled {
    width: 100%;
    left: 0;
    right: 0;
  }
  
  .header.scrolled .navbar {
    border-radius: 0;
    max-width: 100%;
  }

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