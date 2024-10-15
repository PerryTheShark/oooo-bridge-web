<script setup lang="ts">
import Icon from "oooo-components/ui/Icon.vue";
import WalletConnectButton from "@/components/layout/WalletConnectButton.vue";
import { useEVMWallet } from "oooo-components/oooo-wallet";
import ArrowRightIcon from "./ArrowRightIcon.vue";

defineOptions({ name: "TaskItem" });

defineProps<{
  icon?: string;
  image?: string;
  title?: string;
  description?: string;
  hints?: string[];
  succeed?: boolean;
  dateText?: string;
}>();

const { address } = useEVMWallet();
</script>

<template>
  <div
    class="flex flex-col md:flex-row md:items-center md:justify-between gap-[24px] md:gap-[40px] px-[16px] py-[26px] min-h-[110px] rounded-[2px] border border-[#28292a]"
  >
    <div class="flex items-start md:items-center w-full">
      <Icon v-if="icon" class="shrink-0 mr-[16px] text-[44px]" :name="icon" />
      <img v-if="image" class="shrink-0 mr-[16px] w-[44px]" :src="image" />
      <div class="flex flex-col w-full">
        <div class="flex flex-row items-start justify-between w-full">
          <slot name="title">
            <span class="flex-1">{{ title }}</span>
          </slot>
          <slot name="dateText">
            <span class="flex-1 text-right">{{ dateText }}</span>
          </slot>
        </div>

        <slot name="description">
          <p
            v-if="description"
            class="mt-[4px] text-[12px] font-light text-[#787878] tracking-[0.6px]"
          >
            {{ description }}
          </p>
        </slot>
        <div class="flex flex-row items-start justify-between w-full">
          <div class="flex flex-row gap-[8px]" v-if="hints">
            <div
              v-for="(item, index) in hints"
              :key="index"
              class="border border-[#8a3f0e] text-[#8a3f0e] bg-[#bf8a65] px-[8px] py-[4px] rounded-full"
            >
              {{ item }}
            </div>
          </div>
          <Button
            class="w-full md:w-[50px] bg-[#32CD32] text-white px-[8px] py-[4px] rounded-full flex justify-center"
          >
            <ArrowRightIcon />
          </Button>
        </div>
      </div>
    </div>
    <!-- <div class="shrink-0 flex flex-col justify-end gap-[8px]">
      <template v-if="address">
        <Icon v-if="succeed" name="Finish" class="text-[22px] text-[#abeec4]" />
        <slot v-else />
      </template>
      <WalletConnectButton class="w-full md:w-[172px]" v-else />
    </div> -->
  </div>
</template>

<style lang="scss" scoped></style>
