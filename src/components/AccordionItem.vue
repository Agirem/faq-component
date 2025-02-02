<template>
  <div class="accordion-item">
    <div 
      class="accordion-header"
      @click="$emit('toggle')"
    >
      <h3>{{ question }}</h3>
      <span class="icon">{{ isOpen ? '−' : '+' }}</span>
    </div>
    
    <div 
      class="accordion-content"
      :class="{ 'open': isOpen }"
    >
      <div class="accordion-content-inner">
        <p><slot></slot></p>
      </div>
    </div>
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
.accordion-item {
  margin-bottom: 1rem;
  border-radius: 12px;
  background-color: white;
  box-shadow: 0px 2px 6px rgba(0, 0, 0, 0.05);
}

.accordion-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.5rem;
  cursor: pointer;
  border-radius: 12px;
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
  max-height: 0;
  overflow: hidden;
  transition: all 0.3s ease-out;
  background-color: #F8F9FC;
  border-bottom-left-radius: 12px;
  border-bottom-right-radius: 12px;
}

.accordion-content.open {
  max-height: 500px;
}

.accordion-content-inner {
  padding: 1.5rem;
  opacity: 0;
  transform: translateY(-10px);
  transition: all 0.3s ease-out;
}

.accordion-content.open .accordion-content-inner {
  opacity: 1;
  transform: translateY(0);
}

.accordion-content-inner p {
  margin: 0;
  color: #64748B;
  line-height: 1.6;
}
</style> 