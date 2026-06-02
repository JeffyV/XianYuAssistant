<script setup lang="ts">
import { ref, computed, onMounted } from 'vue'
import { useRoute, useRouter } from 'vue-router'
import AppLayout from '@/components/layout/AppLayout.vue'
import LoginLayout from '@/components/layout/LoginLayout.vue'

const route = useRoute()
const router = useRouter()

const isReady = ref(false)

onMounted(async () => {
  await router.isReady()
  isReady.value = true
})

const isLoginPage = computed(() => route.path === '/login')
</script>

<template>
  <template v-if="isReady">
    <LoginLayout v-if="isLoginPage" />
    <AppLayout v-else />
  </template>
</template>

<style>
html {
  overflow-y: scroll;
}

body {
  overflow-x: hidden;
}
</style>
