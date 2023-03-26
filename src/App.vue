<script setup></script>

<template>
  <header>
    <div class="flex justify-center">
      <img
        @click="redirect()"
        alt="My Logo"
        class="cursor-pointer"
        src="@/assets/my-logo.png"
        width="125"
        height="125"
      />
    </div>
  </header>

  <RouterView />
</template>

<script>
export default {
  methods: {
    redirect() {
      location.href = 'https://kennethsolomon.cyou'
    }
  }
}
</script>
