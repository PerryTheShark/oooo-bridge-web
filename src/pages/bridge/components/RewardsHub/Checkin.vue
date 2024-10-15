<script setup lang="ts">
import { ref, computed } from "vue";
import Icon from "oooo-components/ui/Icon.vue";
import CalendarIcon from "./CalendarIcon.vue";
import CheckIcon from "./CheckIcon.vue";
import DiamondIcon from "./DiamondIcon.vue";
import CheckinIcon from "./CheckinIcon.vue";
const today = new Date();
const days = ref<Array<{ date: Date; label: string }>>([]);

for (let i = -3; i <= 3; i++) {
  const date = new Date(today);
  date.setDate(today.getDate() + i);
  days.value.push({
    date,
    label: `${date.getMonth() + 1}.${date.getDate()}`, // Format month.date
  });
}

const showDialog = ref(false);
const randomText = ref("");

const openDialog = () => {
  randomText.value = Math.random().toString(36).substring(7); // Generate random text
  showDialog.value = true;
};

const closeDialog = () => {
  showDialog.value = false;
};
</script>

<template>
<div class="flex justify-between space-x-2 mt-8">
  <div
    v-for="(day, index) in days"
    :key="index"
    :class="[ 
      'rounded-lg cursor-pointer flex flex-col items-center justify-between flex-1 border-2',
      index < 3 ? 'text-gray-400 cursor-not-allowed border-[#5a660] opacity-50' : '',
      index === 3 ? 'text-white border-pink-300' : '',
      index > 3 ? 'text-gray-400 cursor-not-allowed border-[#5a660]' : '',
    ]"
    @click="index === 3 ? openDialog() : null"
  >
    <div class="flex flex-col items-center justify-between w-full h-3/4 p-4">
      <div v-if="index < 2" class="flex flex-col items-center justify-center h-full">
        <div class="flex items-center justify-center h-4/6">
          <CalendarIcon />
        </div>
        <div class="flex items-center justify-center h-2/6 mt-2">
          <span class="text-sm text-green-500 mt-2"></span>
        </div>
      </div>
      <div v-else-if="index === 2" class="flex flex-col items-center justify-center h-full">
        <div class="flex items-center justify-center h-4/6">
          <CheckIcon />
        </div>
        <div class="flex items-center justify-center h-2/6 mt-2">
          <span class="text-sm text-green-500 mt-2"></span>
        </div>
      </div>
      <div v-else-if="index === 3" class="flex flex-col items-center justify-center h-full">
        <div class="flex items-center justify-center h-4/6">
          <CheckinIcon />
        </div>
        <div class="flex items-end justify-center h-2/6 mt-2">
          <span class="text-sm text-green-500">+14 Gem</span>
        </div>
      </div>
      <div v-else class="flex flex-col items-center justify-center h-full">
        <div class="flex items-center justify-center h-4/6">
          <DiamondIcon />
        </div>
        <div class="flex items-end justify-center h-2/6 mt-2">
          <span class="text-sm text-green-500">+14 Gem</span>
        </div>
      </div>
    </div>
    <div
      :class="[ 
        'flex items-center justify-center w-full h-1/4',
        index === 3 ? 'bg-pink-600' : (index < 3 ? 'bg-[#d1d5db]' : 'bg-[#6c6e70]')
      ]"
    >
      {{ day.label }}
    </div>
  </div>
</div>

  <div
    v-if="showDialog"
    class="fixed inset-0 flex items-center justify-center bg-black bg-opacity-50"
  >
    <div class="p-8 rounded-lg shadow-lg">
      <p>{{ randomText }}</p>
      <button
        @click="closeDialog"
        class="mt-4 bg-blue-500 text-white px-4 py-2 rounded"
      >
        Close
      </button>
    </div>
  </div>
</template>

<style scoped>
.cursor-not-allowed {
  pointer-events: none;
}
</style>
