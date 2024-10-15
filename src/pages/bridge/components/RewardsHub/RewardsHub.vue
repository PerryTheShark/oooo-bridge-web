<script setup lang="ts">
import { OContainer, OHeaderPlus, OContent } from "@/components/OContainer";
import WalletConnectButton from "@/components/layout/WalletConnectButton.vue";
import PageLoading from "@/components/PageLoading.vue";
import { useConfig } from "@/pages/bridge/hooks/use-config.ts";
import Task from "./Task.vue";
import TaskCard from "./TaskCard.vue";
import Checkin from "./Checkin.vue";
const { initializing } = useConfig();
</script>

<template>
  <OContainer class="oooo-rewards-hub">
    <OHeaderPlus title="_ REWARDS HUB" isClose>
      <div
        class="flex flex-col md:flex-row md:items-center justify-between mt-[20px] md:mt-0 md:mr-auto"
      >
        <p
          class="mr-[8px] text-[14px] md:text-base text-[#a4a4a4] -tracking-tighter"
        >
          YOUR ACCOUNT:
        </p>
        <WalletConnectButton />
      </div>
    </OHeaderPlus>

    <OContent>
      <h2 class="-tracking-tighter">DAILY CHECK-IN</h2>
      <Checkin />
    </OContent>

    <OContent>
      <h2 class="-tracking-tighter">QUESTS</h2>
      <div class="flex flex-col md:items-center md:my-4 md:justify-start">
        <Task class="w-full" />
        <Task class="w-full" />
        <Task class="w-full" />
      </div>
    </OContent>
  </OContainer>
</template>

<style scoped>
h1 {
  color: #42b983;
}
</style>
