<template>
  <div>
    <div class="accordion-header" @click="$emit('toggle')">
      <h3>{{ question }}</h3>
      <span class="icon">{{ isOpen ? '−' : '+' }}</span>
    </div>
    
    <transition name="slide">
      <div 
        v-show="isOpen"
        class="accordion-content"
      >
        <div class="accordion-content-inner">
          <p><slot></slot></p>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  name: 'AccordionItem',
  props: {
    question: {
      type: String,
      required: true
    },
    isOpen: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style scoped>
.accordion-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.75rem 1.5rem;
  cursor: pointer;
  border-radius: 12px;
  background-color: white;
  border: 1px solid #F1F5F9;
  margin-bottom: 0.5rem;
}

.accordion-header h3 {
  margin: 0;
  font-size: 1.125rem;
  font-weight: 500;
  color: #1E293B;
}

.icon {
  font-size: 1.25rem;
  color: #000;
  font-weight: 400;
  width: 24px;
  height: 24px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.accordion-content {
  background-color: #F8F9FC;
  border-radius: 12px;
}

.accordion-content-inner {
  padding: 1.25rem 1.5rem;
}

.accordion-content-inner p {
  margin: 0;
  color: #64748B;
  line-height: 1.6;
}

.slide-enter-active,
.slide-leave-active {
  transition: all 0.3s ease-out;
  max-height: 300px;
}

.slide-enter-from,
.slide-leave-to {
  max-height: 0;
  opacity: 0;
  transform: translateY(-10px);
}

.slide-enter-to,
.slide-leave-from {
  max-height: 300px;
  opacity: 1;
  transform: translateY(0);
}
</style> 