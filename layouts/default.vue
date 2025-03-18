<template>
  <div class="layout">
    <Navbar />
    <main>
      <slot />
    </main>
    <Footer />
  </div>
</template>

<script setup>
import Navbar from '~/components/sections/Navbar.vue';
import Footer from '~/components/sections/Footer.vue';
</script>

<style scoped>
.layout {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

main {
  flex: 1;
  margin-top: 80px; /* To account for the fixed navbar */
}
</style> 