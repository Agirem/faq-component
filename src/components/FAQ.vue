<template>
  <div class="max-w-2xl w-full mx-4 bg-white rounded-xl shadow-sm p-8">
    <h1 class="text-3xl font-bold mb-8 text-center">Questions fréquemment posées</h1>
    
    <div class="space-y-4">
      <AccordionItem
        v-for="(faq, index) in faqs"
        :key="index"
        :question="faq.question"
        :is-open="faq.isOpen"
        @toggle="toggleFaq(index)"
      >
        {{ faq.answer }}
      </AccordionItem>
    </div>
  </div>
</template>

<script>
import AccordionItem from './AccordionItem.vue'

export default {
  name: 'FAQ',
  components: {
    AccordionItem
  },
  data() {
    const loremAnswer = "Lorem ipsum dolor sit amet consectetur. Quam lectus tellus non nunc rutrum. Sed semper luctus scelerisque ornare sed pretium amet massa diam."
    return {
      faqs: [
        {
          question: "C'est quoi UIComponent_2025 ?",
          answer: loremAnswer,
          isOpen: false
        },
        {
          question: "Mot de passe oublié ?",
          answer: loremAnswer,
          isOpen: false
        },
        {
          question: "Comment réinitialiser mon compte ?",
          answer: loremAnswer,
          isOpen: false
        },
        {
          question: "DeepSeek Vs ChatGPT ?",
          answer: loremAnswer,
          isOpen: false
        }
      ]
    }
  },
  methods: {
    async toggleFaq(index) {
      // D'abord, on ferme l'accordéon ouvert s'il y en a un
      const openIndex = this.faqs.findIndex(faq => faq.isOpen)
      if (openIndex !== -1 && openIndex !== index) {
        this.faqs[openIndex].isOpen = false
        // On attend un peu que l'animation de fermeture se termine
        await new Promise(resolve => setTimeout(resolve, 300))
      }
      
      // Ensuite, on ouvre/ferme l'accordéon cliqué
      this.faqs[index].isOpen = !this.faqs[index].isOpen
    }
  }
}</script> 