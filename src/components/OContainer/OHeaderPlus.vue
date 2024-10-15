<script setup lang="ts">
import Icon from "oooo-components/ui/Icon.vue";

defineProps<{
  isClose?: boolean;
  title?: string;
}>();
defineEmits<{
  close: [];
}>();
</script>

<template>
  <div
    class="relative border-b border-b-[#5a6960] py-[16px] px-[16px] md:px-[40px]"
  >
    <div class="flex flex-col">
      <div class="flex flex-row items-center justify-between md:mb-[8px]">
        <p class="text-[20px] xl:text-[22px] tracking-[1px]">
          {{ title }}
        </p>
        <p
          class="text-[14px] md:text-[16px] text-[#a4a4a4] tracking-[1px] cursor-pointer"
          v-if="isClose"
          @click="$emit('close')"
        >
          <Icon name="close" />
        </p>
      </div>
      <slot />
    </div>
  </div>
</template>
