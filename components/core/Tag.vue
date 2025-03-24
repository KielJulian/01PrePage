<template>
  <button 
    class="tag" 
    :class="[tagClass, { active: isActive }]"
    @click="$emit('click')"
  >
    {{ text }}
  </button>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
  text: {
    type: String,
    required: true
  },
  isActive: {
    type: Boolean,
    default: false
  }
});

defineEmits(['click']);

// Custom styling based on tag text
const tagClass = computed(() => {
  const tag = props.text.toLowerCase();
  
  // Define tag-specific styles
  const tagStyles = {
    'diagnostik': 'tag-diagnostics',
    'herzkreislauf': 'tag-heart',
    'lunge': 'tag-lung',
    'vorsorge': 'tag-prevention',
    'krebs': 'tag-cancer',
    'igel': 'tag-igel',
    'immunsystem': 'tag-immune',
    'naturheilkunde': 'tag-natural',
    'ernährung': 'tag-nutrition',
    'schmerztherapie': 'tag-pain'
  };
  
  return tagStyles[tag] || 'tag-default';
});
</script>

<style scoped>
.tag {
  padding: 6px 12px;
  border-radius: var(--radius-button, 4px);
  border: 1px solid var(--color-card-boarder);
  color: var(--color-text);
  cursor: pointer;
  font-size: var(--font-size-sm, 0.875rem);
  transition: all 0.2s ease;
}

.tag:hover:not(.active) {
  filter: brightness(0.9);
}

.tag.active {
  border-color: var(--color-primary);
}

/* Tag-specific styles */
.tag-diagnostics {
  background-color: var(--color-tag-diagnostics);
}

.tag-heart {
  background-color: var(--color-tag-heart);
}

.tag-lung {
  background-color: var(--color-tag-lung);
}

.tag-prevention {
  background-color: var(--color-tag-prevention);
}

.tag-cancer {
  background-color: var(--color-tag-cancer);
}

.tag-igel {
  background-color: var(--color-tag-igel);
}

.tag-immune {
  background-color: var(--color-tag-immune);
}

.tag-natural {
  background-color: var(--color-tag-natural);
}

.tag-nutrition {
  background-color: var(--color-tag-nutrition);
}

.tag-pain {
  background-color: var(--color-tag-pain);
}

.tag-default {
  background-color: var(--color-tag-default);
}

/* Active state overrides specific colors */
.tag.active.tag-diagnostics { background-color: #94b4f0; }
.tag.active.tag-heart       { background-color: #f5a3a3; }
.tag.active.tag-lung        { background-color: #94d3ef; }
.tag.active.tag-prevention  { background-color: #8ee5c1; }
.tag.active.tag-cancer      { background-color: #c7a6e3; }
.tag.active.tag-igel        { background-color: #f7c887; }
.tag.active.tag-immune      { background-color: #f4bd67; }
.tag.active.tag-natural     { background-color: #f5da87; }
.tag.active.tag-nutrition   { background-color: #f8d97a; }
.tag.active.tag-pain        { background-color: #f29b8e; }
.tag.active.tag-default     { background-color: #f3c896; }
</style> 