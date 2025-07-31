<script setup lang="ts">
import Button from './components/Button.vue'
import { ref } from 'vue'

const loading = ref(false)
</script>

<template>
  <div class="flex h-screen w-screen items-center justify-center">
    <Button :loading="loading" @click="loading = true" color="error">
      asdasfasdfsadsafasdasfdasdfassafdsadsadsadsadasdsa
    </Button>
  </div>
</template>
