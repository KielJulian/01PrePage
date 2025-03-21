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
  background-color: var(--color-background-alt, #f5f5f5);
  border: 1px solid var(--color-border, #e0e0e0);
  color: var(--color-text, #555);
  cursor: pointer;
  font-size: var(--font-size-sm, 0.875rem);
  transition: all 0.2s ease;
}

.tag:hover:not(.active) {
  background-color: var(--color-white);
}

.tag.active {
  background-color: var(--color-primary);
  color: white;
  border-color: var(--color-primary);
}

/* Tag-specific styles */
.tag-diagnostics {
  border-color: #3498db;
  color: #3498db;
}

.tag-heart {
  border-color: #e74c3c;
  color: #e74c3c;
}

.tag-lung {
  border-color: #3498db;
  color: #3498db;
}

.tag-prevention {
  border-color: #2ecc71;
  color: #2ecc71;
}

.tag-cancer {
  border-color: #9b59b6;
  color: #9b59b6;
}

.tag-igel {
  border-color: #f39c12;
  color: #f39c12;
}

.tag-immune {
  border-color: #27ae60;
  color: #27ae60;
}

.tag-natural {
  border-color: #16a085;
  color: #16a085;
}

.tag-nutrition {
  border-color: #f1c40f;
  color: #f1c40f;
}

.tag-pain {
  border-color: #c0392b;
  color: #c0392b;
}

.tag-default {
  border-color: #95a5a6;
  color: #95a5a6;
}

/* Active state overrides specific colors */
.tag.active.tag-diagnostics { background-color: #3498db; color: white; }
.tag.active.tag-heart { background-color: #e74c3c; color: white; }
.tag.active.tag-lung { background-color: #3498db; color: white; }
.tag.active.tag-prevention { background-color: #2ecc71; color: white; }
.tag.active.tag-cancer { background-color: #9b59b6; color: white; }
.tag.active.tag-igel { background-color: #f39c12; color: white; }
.tag.active.tag-immune { background-color: #27ae60; color: white; }
.tag.active.tag-natural { background-color: #16a085; color: white; }
.tag.active.tag-nutrition { background-color: #f1c40f; color: white; }
.tag.active.tag-pain { background-color: #c0392b; color: white; }
.tag.active.tag-default { background-color: #95a5a6; color: white; }
</style> 