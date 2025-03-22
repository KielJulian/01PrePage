<template>
  <div>
    
    <TopCard />
    <LeistungSection />
    <PraxisSection />
    <TeamSection />
    <KontaktSection />
    <MapSection />
    
  </div>
</template>

<script setup>
import TopCard from '~/components/core/TopCard.vue';
import LeistungSection from '~/components/sections/LeistungSection.vue';
import PraxisSection from '~/components/sections/PraxisSection.vue';
import TeamSection from '~/components/sections/TeamSection.vue';
import KontaktSection from '~/components/sections/KontaktSection.vue';
import MapSection from '~/components/sections/MapSection.vue';
definePageMeta({
  layout: 'default'
})
</script>
