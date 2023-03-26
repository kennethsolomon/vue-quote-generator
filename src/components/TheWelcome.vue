<script setup>
import WelcomeItem from './WelcomeItem.vue'
import IconQuote from './icons/IconQuote.vue'
</script>

<template>
  <WelcomeItem>
    <template #icon>
      <IconQuote class="cursor-pointer" @click="refreshQuote()" />
    </template>
    <template #heading>Quote of the Day 💬</template>
    <p>{{ quote.split('—')[0] }}</p>
    <p>{{ '— ' + quote.split('—')[1] }}</p>
  </WelcomeItem>
</template>

<script>
export default {
  data: () => ({
    quote: 'Hello v2'
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
