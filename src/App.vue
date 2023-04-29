<script setup lang="ts">
import { onMounted, ref } from 'vue';
import SkeletonLoader from './components/SkeletonLoader.vue';

const loading = ref(true)

onMounted(() => {
  setTimeout(() => {
    loading.value = false
  }, 3000)
})
</script>

<template>
  <div>
    <div v-if="loading">
      <SkeletonLoader class="h-screen w-full grid place-content-center text-gray-500 text-8xl font-bold italic">
        <div>LOADING...</div>
      </SkeletonLoader>
    </div>

    <div class="grid place-content-center gap-5 h-screen" v-else>
      <p class="text-center">EXAMPLE:</p>
      <div class="w-80 space-y-2">
        <SkeletonLoader class="h-40 rounded-lg" bg-color="#CCCCCC" shimmer-color="#eeeeee" />
        <div class="flex items-start gap-3">
          <SkeletonLoader class="w-10 h-10 rounded-full" bg-color="#E2E2E2" />
          <div class="flex-1 space-y-2 mr-8">
            <SkeletonLoader class="h-4" bg-color="#E2E2E2" />
            <SkeletonLoader class="h-4 mr-10" bg-color="#E2E2E2" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
