<template>
    <div v-if="prizeData">
        <h3 class="text-xl">🎁 {{ prizeData.name }}</h3>
        <p>จำนวนรางวัลทั้งหมด: {{ prizeData.quantity }}</p>
        <img :src="prizeData.image_url" :alt="prizeData.name" class="mx-auto w-48 h-48 object-cover rounded" />
        <div>
            <button class="btn btn-primary mt-10" @click="$emit('startDrawing')" :disabled="isDrawing">
                สุ่ม {{ drawQuantity }} คน
            </button>
        </div>
    </div>
</template>

<script setup>
defineProps(['prizeData', 'drawQuantity', 'isDrawing'])
</script>