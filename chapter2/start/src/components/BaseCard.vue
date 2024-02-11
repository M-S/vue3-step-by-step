<script setup lang="ts">
import { type PropType, onMounted } from 'vue';
import type { TAdvert } from '@/types/common';
const props = defineProps({
  details: {
    type: Object as PropType<TAdvert>,
    required: true
  }
});
onMounted(() => {
  console.log('details', props.details);
});
</script>
<template>
  <div class="card">
    <div class="card-image">
      <figure class="image is-4by3">
        <img :src="details.imageSrc" :alt="details.place" />
      </figure>
    </div>
    <div class="card-content">
      <p>
        <span class="title is-4 has-text-dark">{{ details.place }}</span>
      </p>
      <p>
        <span>from </span><span class="subtitle is-1 has-text-info">{{ details.price }}</span>
      </p>

      <div class="card-footer-item">
        {{ details.description }}
      </div>
    </div>
  </div>
</template>

<style scoped>
</style>
