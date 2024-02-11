<script setup lang="ts">
import BaseCard from './BaseCard.vue';
import { ref, onMounted } from 'vue';
import type { TAdvert } from '@/types/common';
const fetchAdverts = async (): Promise<TAdvert[]> => {
  const response = await fetch('/api/adverts');
  const data = await response.json();
  return data.adverts;
};
const adverts = ref<TAdvert[]>([
  {
    description:
      'Confido coerceo cervus textor ullam. Dicta textus iste solum adinventitias voluntarius demens canis termes. Sequi eius esse bestia subiungo vester ascisco damno tersus.',
    imageSrc: 'https://loremflickr.com/640/480/places?lock=7605039057076224',
    price: '$ 242',
    place: 'North Filibertofort',
    id: '1'
  },
  {
    description:
      'Subiungo atrocitas comburo. Confero statim supellex caveo tepesco. Tam consequatur surculus blanditiis velociter talus blandior.',
    imageSrc: 'https://loremflickr.com/640/480/places?lock=5086963730219008',
    price: '$ 377',
    place: 'Erie',
    id: '2'
  },
  {
    description:
      'Inflammatio cado videlicet conservo cunabula. Coniecto peior certe. Aureus allatus tabesco.',
    imageSrc: 'https://loremflickr.com/640/480/places?lock=1731523577380864',
    price: '$ 411',
    place: 'Skilesfurt',
    id: '3'
  }
]);
onMounted(async () => {
  adverts.value = await fetchAdverts();
});
</script>
<template>
  <div v-if="adverts" class="columns">
    <div class="column" v-for="(item, i) in adverts" :key="i">
      <BaseCard :details="item"></BaseCard>
    </div>
  </div>
</template>
