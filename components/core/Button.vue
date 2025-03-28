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
  border-radius: var(--radius-button);
  font-weight: 600;
  font-size: 1rem;
  padding: 10px 14px 10px 14px;
  cursor: pointer;
  transition: all 0.3s ease;
  border: none;
  outline: none;
  font-size: var(--font-size-base);
  font-weight: var(--font-weight-semibold);
}

.btn-primary {
  background-color: var(--color-primary);
  background-size: 100% auto;
  color: var(--color-white);
}

.btn-primary:hover {
  background-position: right center;
  background-size: 200% auto;
  animation: main 1.5s infinite;
}

.btn-secondary {
  background-color: var(--color-accent-green);
  background-size: 100% auto;
  color: var(--color-white);
}

.btn-secondary:hover {
  background-position: right center;
  background-size: 200% auto;
  animation: secondary 1.5s infinite;
}

.btn-outline {
  background-color: transparent;
  color: var(--color-primary);
  border: 2px solid var(--color-primary);
}

.btn-outline:hover {
  background-color: var(--color-primary);
  animation: main 1.5s infinite;
}

.btn-large {
  padding: 1rem 2rem;
  font-size: 1.1rem;
}

@keyframes main {
  0% {
    box-shadow: 0 0 0 0 rgba(var(--color-primary-rgb), 0.4);
  }
  70% {
    box-shadow: 0 0 0 10px rgba(var(--color-primary-rgb), 0);
  }
  100% {
    box-shadow: 0 0 0 0 rgba(var(--color-primary-rgb), 0);
  }
}

@keyframes secondary {
  0% {
    box-shadow: 0 0 0 0 rgba(var(--color-accent-green-rgb), 0.4);
  }
  70% {
    box-shadow: 0 0 0 10px rgba(var(--color-accent-green-rgb), 0);
  }
  100% {
    box-shadow: 0 0 0 0 rgba(var(--color-accent-green-rgb), 0);
  }
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