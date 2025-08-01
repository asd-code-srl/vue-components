<script setup lang="ts">
import Button from './components/Button.vue'
import { ref } from 'vue'

const loading1 = ref(false)
const loading2 = ref(false)
</script>

<template>
  <div class="flex h-screen w-screen items-center justify-center gap-5">
    <Button :loading="loading1" @click="loading1 = true" color="default">
      <template #leftIcon>A</template>
      <span>Trimite</span>
    </Button>
    <Button
      :loading="loading1"
      @click="loading1 = true"
      color="default"
      variant="ghost"
      size="md"
    >
      <template #leftIcon>A</template>
      <span>Trimite</span>
    </Button>
    <Button
      :loading="loading2"
      @click="loading2 = true"
      color="info"
      rounded="full"
      variant="outline"
      size="lg"
      >Cerere </Button
    ><Button
      :loading="loading2"
      @click="loading2 = true"
      color="info"
      rounded="full"
      variant="text"
      size="lg"
      >Cerere
    </Button>
  </div>
</template>
