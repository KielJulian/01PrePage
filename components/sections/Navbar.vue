<template>
  <header class="header" :class="{ 'scrolled': isScrolled }" v-show="isReady">
    <div class="navbar" :class="{ 'expanded': mobileMenuActive }" ref="navbarRef">
      <!-- Logo and Hamburger section always visible -->
      <div class="navbar-main">
        <div class="logo">
          <img src="/public/img/icons/logo.svg" alt="Logo">
          <span v-if="mobileMenuActive" class="logo-text">01PrePage</span>
        </div>
        
        <!-- Desktop Navigation -->
        <nav class="nav-menu" v-if="!isMobile">
          <ul class="nav-list" ref="navListRef">
            <li class="nav-item">
              <a href="#" class="nav-link" :class="{ 'active': activeSection === 'home' }" @click.prevent="scrollToSection('home')">Home</a>
            </li>
            <li class="nav-item">
              <a href="#leistungen" class="nav-link" :class="{ 'active': activeSection === 'leistungen' }" @click.prevent="scrollToSection('leistungen')">Leistungen</a>
            </li>
            <li class="nav-item">
              <a href="#praxis" class="nav-link" :class="{ 'active': activeSection === 'praxis' }" @click.prevent="scrollToSection('praxis')">Praxis</a>
            </li>
            <li class="nav-item">
              <a href="#team" class="nav-link" :class="{ 'active': activeSection === 'team' }" @click.prevent="scrollToSection('team')">Team</a>
            </li>
            <li class="nav-item">
              <a href="#kontakt" class="nav-link" :class="{ 'active': activeSection === 'kontakt' }" @click.prevent="scrollToSection('kontakt')">Kontakt</a>
            </li>
            <div class="nav-indicator" :style="indicatorStyle"></div>
          </ul>
        </nav>
        
        <div class="nav-right">
          <Button v-if="!isMobile" class="main-button">Termin vereinbaren</Button>
          <div class="menu-toggle" @click="toggleMobileMenu">
            <div class="bar" :class="{ 'active': mobileMenuActive }"></div>
            <div class="bar" :class="{ 'active': mobileMenuActive }"></div>
            <div class="bar" :class="{ 'active': mobileMenuActive }"></div>
          </div>
        </div>
      </div>
      
      <!-- Mobile Dropdown Content -->
      <div class="dropdown-content" :class="{ 'visible': mobileMenuActive }">
        <ul class="dropdown-list">
          <li class="dropdown-item">
            <a href="#" class="dropdown-link" @click.prevent="scrollToSectionAndCloseMenu('home')">Home</a>
          </li>
          <li class="dropdown-item">
            <a href="#leistungen" class="dropdown-link" @click.prevent="scrollToSectionAndCloseMenu('leistungen')">Leistungen</a>
          </li>
          <li class="dropdown-item">
            <a href="#praxis" class="dropdown-link" @click.prevent="scrollToSectionAndCloseMenu('praxis')">Praxis</a>
          </li>
          <li class="dropdown-item">
            <a href="#team" class="dropdown-link" @click.prevent="scrollToSectionAndCloseMenu('team')">Team</a>
          </li>
          <li class="dropdown-item">
            <a href="#kontakt" class="dropdown-link" @click.prevent="scrollToSectionAndCloseMenu('kontakt')">Kontakt</a>
          </li>
        </ul>
        <div class="dropdown-footer">
          <Button v-if="isMobile" class="main-button" @click="closeMenu">Termin vereinbaren</Button>
        </div>
      </div>
    </div>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted, computed, watch, nextTick } from 'vue';
import Button from '../core/Button.vue';
import { useRoute, useRouter } from 'vue-router';

const route = useRoute();
const router = useRouter();
const isScrolled = ref(false);
const mobileMenuActive = ref(false);
const isMobile = ref(false);
const navbarRef = ref(null);
const activeSection = ref('');
const navListRef = ref(null);
const isReady = ref(false);
const indicatorStyle = ref({
  width: '0px',
  transform: 'translateX(0px)'
});

// Check if we're on the home page or another page
const isHomePage = computed(() => {
  return route.path === '/' || route.path === '/index';
});

// Add watcher for route changes to handle page navigation
watch(route, () => {
  if (!isHomePage.value) {
    // When on a different page like Impressum, clear active section
    activeSection.value = '';
    // Reset the indicator
    indicatorStyle.value = {
      width: '0px',
      transform: 'translateX(0px)'
    };
  } else {
    // When returning to homepage, check which section is active
    checkActiveSection();
  }
});

// Add a scroll offset value (adjust as needed)
const scrollOffset = ref(100); // This value represents pixels from the top

const handleScroll = () => {
  // Only apply scroll effect if not on mobile
  if (!isMobile.value) {
    isScrolled.value = window.scrollY > 50;
  }
  
  // Check which section is currently visible
  checkActiveSection();
};

const checkActiveSection = () => {
  const sections = ['home', 'leistungen', 'praxis', 'team', 'kontakt'];
  
  // Home section is special case - set no active section
  if (window.scrollY < 100) {
    activeSection.value = ''; // Set to empty instead of 'home'
    updateIndicator();
    return;
  }
  
  // Check other sections
  for (const section of sections) {
    if (section === 'home') continue;
    
    const element = document.getElementById(section);
    if (element) {
      const rect = element.getBoundingClientRect();
      // Get the middle point of the viewport
      const viewportMiddle = window.innerHeight / 2;
      
      // Consider a section active when it crosses the middle of the screen
      if (rect.top <= viewportMiddle && rect.bottom >= viewportMiddle) {
        activeSection.value = section;
        updateIndicator();
        return;
      }
    }
  }
};

const updateIndicator = () => {
  if (!navListRef.value) return;
  
  const activeLink = navListRef.value.querySelector(`.nav-link.active`);
  if (activeLink) {
    const linkRect = activeLink.getBoundingClientRect();
    const navListRect = navListRef.value.getBoundingClientRect();
    
    indicatorStyle.value = {
      width: `${linkRect.width}px`,
      transform: `translateX(${linkRect.left - navListRect.left}px)`
    };
  }
};

const checkMobile = () => {
  isMobile.value = window.innerWidth <= 900;
  // Reset scroll effect if mobile
  if (isMobile.value) {
    isScrolled.value = false;
  } else {
    isScrolled.value = window.scrollY > 50;
    // Update indicator position after resize
    setTimeout(updateIndicator, 100);
  }
};

const toggleMobileMenu = () => {
  mobileMenuActive.value = !mobileMenuActive.value;
};

const closeMenu = () => {
  mobileMenuActive.value = false;
};

const handleClickOutside = (event) => {
  if (mobileMenuActive.value && navbarRef.value && !navbarRef.value.contains(event.target)) {
    mobileMenuActive.value = false;
  }
};

const scrollToSection = (sectionId) => {
  // If we're not on the home page, navigate to the home page first
  if (!isHomePage.value) {
    // Navigate to home page and set target section for scrolling after navigation
    router.push('/');
    // Set active section immediately to update UI
    activeSection.value = sectionId === 'home' ? '' : sectionId;
    
    // Add a small delay to allow navigation to complete before scrolling
    setTimeout(() => {
      scrollToSectionImpl(sectionId);
    }, 100);
    return;
  }
  
  // Otherwise just scroll normally
  scrollToSectionImpl(sectionId);
};

const scrollToSectionImpl = (sectionId) => {
  if (sectionId === 'home') {
    window.scrollTo({
      top: 0,
      behavior: 'smooth'
    });
    return;
  }

  const element = document.getElementById(sectionId);
  if (element) {
    const elementPosition = element.getBoundingClientRect().top;
    const offsetPosition = elementPosition + window.pageYOffset - scrollOffset.value;
    
    window.scrollTo({
      top: offsetPosition,
      behavior: 'smooth'
    });
  }
};

const scrollToSectionAndCloseMenu = (sectionId) => {
  closeMenu();
  scrollToSection(sectionId);
};

onMounted(() => {
  // Delay showing the navbar until everything is ready
  isReady.value = false;
  
  // Set up event listeners
  window.addEventListener('scroll', handleScroll);
  window.addEventListener('resize', checkMobile);
  document.addEventListener('click', handleClickOutside);
  
  // Initial mobile check
  checkMobile();
  
  // Only check active section if we're on the home page
  if (isHomePage.value) {
    checkActiveSection(); // Initial check for active section
  }
  
  // Wait for everything to be ready before showing the navbar
  window.addEventListener('load', () => {
    // Add a small delay to ensure all styles and responsive layouts are applied
    setTimeout(() => {
      isReady.value = true;
      // Initial indicator position after DOM is fully rendered
      nextTick(() => {
        updateIndicator();
      });
    }, 200); // 200ms delay should be enough for most cases
  });
  
  // Fallback in case the load event already fired
  if (document.readyState === 'complete') {
    setTimeout(() => {
      isReady.value = true;
      nextTick(() => {
        updateIndicator();
      });
    }, 200);
  }
});

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll);
  window.removeEventListener('resize', checkMobile);
  document.removeEventListener('click', handleClickOutside);
});
</script>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 1000;
  margin-top: var(--spacing-md);
  background-color: transparent;
  box-sizing: border-box;
}

.header.scrolled {
  background-color: transparent;
  margin-top: var(--spacing-sm);
  width: calc(100% - var(--spacing-md) * 2);
  left: var(--spacing-md);
  right: var(--spacing-md);
  margin-left: 0;
  margin-right: 0;
}

.navbar {
  will-change: transform;
  max-width: var(--navbar-width);
  width: 100%;
  margin: 0 auto;
  background-color: transparent;
  border-radius: 32px;
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
  background-color: transparent;
}

.header.scrolled .navbar {
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
  padding: 12px;
}

.logo {
  display: flex;
  align-items: center;
  justify-content: center;
  width: max-content;
  height: max-content;
  padding-left: 4px;
}

.logo img {
  display: block;
  width: 24px;
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

/* Navbar Hamburger */
.bar {
  width: 25px;
  height: 3px;
  background-color: var(--color-primary);
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
  border-top: 1px solid var(--color-card-boarder);
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
  display: flex;
  flex-direction: column;
  align-items: center;
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
  border-top: 1px solid var(--color-card-boarder);
}

.nav-list {
  display: flex;
  list-style: none;
  gap: var(--spacing-md);
  position: relative;
}

.nav-link {
  color: var(--color-primary);
  font-weight: 500;
  padding: var(--spacing-xs) 0;
  position: relative;
  transition: color 0.3s ease;
}

.nav-link::after {
  content: none;
}

.nav-link:hover {
  color: var(--color-accent-yellow);
}

.nav-link:hover::after {
  width: 100%;
}

.nav-link.active::after {
  width: 100%;
}

/* Add a shared indicator element */
.nav-indicator {
  position: absolute;
  bottom: 0;
  left: 0;
  height: 2px;
  background-color: var(--color-accent-yellow);
  transition: transform 0.3s cubic-bezier(0.34, 1.56, 0.64, 1), 
              width 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
}

@media (max-width: 900px) {
  .header {
    margin-top: var(--spacing-sm);
    width: 100%;
    left: 0;
    right: 0;
  }
  
  .header.scrolled {
    margin-top: var(--spacing-sm);
    width: 100%;
    left: 0;
    right: 0;
  }
  
  .navbar {
    border-radius: 32px;
    max-width: calc(100% - var(--spacing-xs) * 2);
    margin: 0 auto;
    background-color: white !important;
    overflow: hidden;
    box-shadow: 0 4px 12px var(--box-shadow-card);
    border: 1px solid var(--color-card-boarder);
  }
  
  .navbar-main {
    background-color: white;
  }
  
  .navbar.expanded {
    position: relative;
    top: auto;
    left: auto;
    width: auto;
    border-radius: 32px;
    overflow: hidden;
    max-height: none;
  }
  
  .dropdown-content {
    border-top: 1px solid rgba(0, 0, 0, 0.05);
    padding-bottom: var(--spacing-md);
    background-color: white;
  }
  
  .menu-toggle {
    display: flex;
  }
  
  .desktop-only {
    display: none;
  }
  
  .desktop-only.main-button {
    display: none !important;
  }
  
  .navbar.expanded .logo-text {
    display: block;
  }
}

@media (min-width: 901px) {
  .logo-text {
    display: none;
  }
  
  .dropdown-footer .main-button {
    display: none;
  }
}

.main-button {
  display: block;
}
</style> 