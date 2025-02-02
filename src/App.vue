<template>
  <div class="min-h-screen w-full flex items-center justify-center" style="background-color: #EEEEEE;">
    <div class="max-w-2xl w-full mx-4 bg-white rounded-xl shadow-sm p-8">
      <h1 class="text-3xl font-bold mb-8 text-center">Questions fréquemment posées</h1>
      
      <div class="space-y-4">
        <div v-for="(faq, index) in faqs" 
             :key="index">
          <button
            class="w-full px-6 py-4 text-left flex justify-between items-center border rounded-lg"
            @click="toggleFaq(index)"
          >
            <span class="text-lg font-medium text-[#1E293B]">{{ faq.question }}</span>
            <span class="text-xl">{{ faq.isOpen ? '−' : '+' }}</span>
          </button>
          
          <div 
            v-if="faq.isOpen"
            class="mt-2 px-6 py-4 bg-[#F1F5F9] rounded-lg"
          >
            <p class="text-[#64748B]">Lorem ipsum dolor sit amet consectetur. Quam lectus tellus non nunc rutrum. Sed semper luctus scelerisque ornare sed pretium amet massa diam.</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'FaqAccordion',
  data() {
    return {
      faqs: [
        {
          question: "C'est quoi UIComponent_2025 ?",
          isOpen: false
        },
        {
          question: "Mot de passe oublié ?",
          isOpen: false
        },
        {
          question: "Comment réinitialiser mon compte ?",
          isOpen: false
        },
        {
          question: "DeepSeek Vs ChatGPT ?",
          isOpen: false
        }
      ]
    }
  },
  methods: {
    toggleFaq(index) {
      this.faqs = this.faqs.map((faq, i) => ({
        ...faq,
        isOpen: i === index ? !faq.isOpen : false
      }))
    }
  }
}
</script>