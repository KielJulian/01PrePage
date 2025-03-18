<template>
  <header class="header" :class="{ 'scrolled': isScrolled }">
    <div class="navbar" :class="{ 'expanded': mobileMenuActive }">
      <!-- Logo and Hamburger section always visible -->
      <div class="navbar-main">
        <div class="logo">
          <img src="/public/img/icons/logo.svg" alt="Logo">
          <span v-if="mobileMenuActive" class="logo-text">01PrePage</span>
        </div>
        
        <!-- Desktop Navigation -->
        <nav class="nav-menu desktop-only">
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
      
      <!-- Mobile Dropdown Content -->
      <div class="dropdown-content" :class="{ 'visible': mobileMenuActive }">
        <div class="close-button" @click="toggleMobileMenu">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M18 6L6 18" stroke="#133882" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            <path d="M6 6L18 18" stroke="#133882" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </div>
        <ul class="dropdown-list">
          <li class="dropdown-item">
            <a href="#" class="dropdown-link">Home</a>
          </li>
          <li class="dropdown-item">
            <a href="#leistungen" class="dropdown-link">Leistungen</a>
          </li>
          <li class="dropdown-item">
            <a href="#praxis" class="dropdown-link">Praxis</a>
          </li>
          <li class="dropdown-item">
            <a href="#team" class="dropdown-link">Team</a>
          </li>
          <li class="dropdown-item">
            <a href="#kontakt" class="dropdown-link">Kontakt</a>
          </li>
        </ul>
        <div class="dropdown-footer">
          <Button variant="secondary">Termin vereinbaren</Button>
        </div>
      </div>
    </div>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted, computed } from 'vue';
import Button from '../core/Button.vue';

const isScrolled = ref(false);
const mobileMenuActive = ref(false);
const isMobile = ref(false);

const handleScroll = () => {
  // Only apply scroll effect if not on mobile
  if (!isMobile.value) {
    isScrolled.value = window.scrollY > 50;
  }
};

const checkMobile = () => {
  isMobile.value = window.innerWidth <= 900;
  // Reset scroll effect if mobile
  if (isMobile.value) {
    isScrolled.value = false;
  } else {
    isScrolled.value = window.scrollY > 50;
  }
};

const toggleMobileMenu = () => {
  mobileMenuActive.value = !mobileMenuActive.value;
};

onMounted(() => {
  window.addEventListener('scroll', handleScroll);
  window.addEventListener('resize', checkMobile);
  checkMobile(); // Initial check
});

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll);
  window.removeEventListener('resize', checkMobile);
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
  transition: all 0.3s ease;
  max-width: var(--navbar-width);
  width: 100%;
  margin: 0 auto;
  background-color: white;
  border-radius: 32px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  overflow: hidden;
}

.navbar.expanded {
  border-radius: 0;
  max-height: 100vh;
}

.navbar-main {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: var(--spacing-md) var(--spacing-lg);
  background-color: white;
}

.header.scrolled .navbar {
  padding: 0;
  background-color: rgba(255, 255, 255, 0.85);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  border: 1px solid var(--color-card-boarder);
  box-shadow: 
    rgba(0, 0, 0, 0.07) 0px 0.60219px 0.60219px -1.25px,
    rgba(0, 0, 0, 0.063) 0px 2.28853px 2.28853px -2.5px,
    rgba(0, 0, 0, 0.024) 0px 10px 10px -3.75px;
}

.header.scrolled .navbar-main {
  padding: var(--spacing-sm) var(--spacing-md);
}

.logo {
  display: flex;
  align-items: center;
  justify-content: center;
  width: max-content;
  height: max-content;
}

.logo img {
  display: block;
  width: 36px;
  height: auto;
}

.logo-text {
  font-weight: 600;
  font-size: 1.2rem;
  color: var(--color-primary);
  margin-left: var(--spacing-xs);
  display: none;
}

/* For screens smaller than the max navbar width plus margins */
@media (max-width: calc(var(--navbar-width) + var(--spacing-3xl) * 2)) {
  .header.scrolled {
    width: calc(100% - var(--spacing-lg) * 2);
    left: var(--spacing-lg);
    right: var(--spacing-lg);
  }
  
  .header.scrolled .navbar-main {
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

/* Dropdown Styles */
.dropdown-content {
  display: none;
  padding: var(--spacing-lg);
  position: relative;
  border-top: 1px solid rgba(0, 0, 0, 0.05);
}

.dropdown-content.visible {
  display: block;
}

.close-button {
  position: absolute;
  top: var(--spacing-md);
  right: var(--spacing-md);
  cursor: pointer;
}

.dropdown-list {
  list-style: none;
  margin-bottom: var(--spacing-xl);
}

.dropdown-item {
  margin-bottom: var(--spacing-md);
}

.dropdown-link {
  color: var(--color-primary);
  font-weight: 500;
  text-decoration: none;
  font-size: 1.1rem;
  display: block;
  padding: var(--spacing-xs) 0;
}

.dropdown-footer {
  display: flex;
  justify-content: center;
  padding-top: var(--spacing-md);
  margin-top: var(--spacing-md);
  border-top: 1px solid rgba(0, 0, 0, 0.1);
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
  left: 50%;
  width: 0;
  height: 2px;
  transform: translateX(-50%);
  background-color: var(--color-accent-yellow);
  transition: width 0.3s ease;
}

.nav-link:hover::after {
  width: 100%;
}

@media (max-width: 900px) {
  .header {
    margin-top: var(--spacing-lg);
    width: 100%;
    left: 0;
    right: 0;
  }
  
  .header.scrolled {
    margin-top: var(--spacing-lg);
    width: 100%;
    left: 0;
    right: 0;
  }
  
  .navbar {
    border-radius: 32px;
    max-width: calc(100% - var(--spacing-lg) * 2);
    margin: 0 auto;
    background-color: white;
    overflow: hidden;
  }
  
  .navbar.expanded {
    position: relative;
    top: auto;
    left: auto;
    width: auto;
    max-width: calc(100% - var(--spacing-lg) * 2);
    border-radius: 32px;
    overflow: hidden;
  }
  
  .dropdown-content {
    border-top: 1px solid rgba(0, 0, 0, 0.05);
    padding-bottom: var(--spacing-md);
  }
  
  .menu-toggle {
    display: flex;
  }
  
  .desktop-only {
    display: none;
  }
  
  .navbar.expanded .logo-text {
    display: block;
  }
}

@media (min-width: 901px) {
  .logo-text {
    display: none;
  }
}
</style> 