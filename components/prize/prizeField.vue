<script setup lang="ts">
import { usePrizeStore } from '@/stores/PrizeStore';
import PrizesCarousel from './prizesCarousel.vue';


const route = useRoute();
const prizeStore = usePrizeStore();
const roomId = route.params.id as string;

onMounted(async () => {
  await prizeStore.fetchPrizes(roomId);
});

const prizesQuantity = computed(() => prizeStore.prizes.length);

const props = defineProps({
  handleEditPrize: Function
})
</script>

<template>
  <div class="container mx-auto">
    <fieldset class="fieldset bg-base-[#0F172B] p-4">
      <legend class="fieldset-legend">
        <h2 class="text-2xl md:text-3xl mb-2 text-black text-shadow-md">รางวัล ({{ prizesQuantity }} ชิ้น)</h2>
      </legend>
      <PrizesCarousel :handleEditPrize="handleEditPrize" />
    </fieldset>
  </div>
</template>