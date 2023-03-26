<script setup>
import WelcomeItem from './WelcomeItem.vue'
import IconQuote from './icons/IconQuote.vue'
</script>

<template>
  <WelcomeItem v-if="quote">
    <template #icon>
      <IconQuote class="cursor-pointer" @click="refreshQuote()" />
    </template>
    <template #heading>Quote of the day 💬</template>
    <div v-if="quote">
      <p>{{ quote.split('—')[0] }}</p>
      <p>{{ '— ' + quote.split('—')[1] }}</p>
    </div>
  </WelcomeItem>
</template>

<script>
export default {
  data: () => ({
    quote: ''
  }),
  methods: {
    refreshQuote() {
      this.getQuote()
    },
    getQuote() {
      fetch('https://api.kennethsolomon.cyou/api/quote')
        .then((response) => response.json())
        .then((data) => (this.quote = data.data))
    }
  },
  mounted() {
    this.getQuote()
  }
}
</script>
