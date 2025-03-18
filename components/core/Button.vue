<template>
  <button 
    class="btn" 
    :class="[
      `btn-${variant}`, 
      { 'btn-large': large }
    ]"
    @click="$emit('click')"
  >
    <slot></slot>
  </button>
</template>

<script setup>
defineProps({
  variant: {
    type: String,
    default: 'primary',
    validator: (value) => ['primary', 'secondary', 'outline'].includes(value)
  },
  large: {
    type: Boolean,
    default: false
  }
})

defineEmits(['click'])
</script>

<style scoped>
.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  border-radius: var(--radius-small);
  font-weight: 600;
  font-size: 1rem;
  padding: 0.75rem 1.5rem;
  cursor: pointer;
  transition: all 0.3s ease;
  border: none;
  outline: none;
}

.btn-primary {
  background-color: var(--color-primary);
  color: var(--color-white);
}

.btn-primary:hover {
  background-color: #0e2a68;
}

.btn-secondary {
  background-color: var(--color-accent-yellow);
  color: var(--color-primary);
}

.btn-secondary:hover {
  background-color: #f1c287;
}

.btn-outline {
  background-color: transparent;
  color: var(--color-primary);
  border: 2px solid var(--color-primary);
}

.btn-outline:hover {
  background-color: rgba(19, 56, 130, 0.1);
}

.btn-large {
  padding: 1rem 2rem;
  font-size: 1.1rem;
}

@media (max-width: 768px) {
  .btn {
    padding: 0.6rem 1.2rem;
    font-size: 0.9rem;
  }
  
  .btn-large {
    padding: 0.8rem 1.6rem;
    font-size: 1rem;
  }
}
</style> 